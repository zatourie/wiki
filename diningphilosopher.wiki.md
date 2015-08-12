발제자 : 심민규

# Dining Philosopher

![http://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Dining_philosophers.png/200px-Dining_philosophers.png](http://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Dining_philosophers.png/200px-Dining_philosophers.png)

## Lock

http://www.snow.or.kr/lecture/applied_sciences/computer_science/1212.html

```
//#1
Semaphore forks[] = {1,1,1,1,1}

void Philosopher(int id)
{
    for ( int i = 0 ; i < 3 ; i++ ) {
	    think();
		SW(forks[id]);
		SW(forks[(id+1)];
		Eat();
		SS(forks[id]);
		SS(forks[(id+1)%5]);
	}
	think();
}

//#2
Semaphore forks[] = {1,1,1,1,1}

Semaphore numAllowedToEat(2);

void Philosopher(int id)
{
    for ( int i = 0 ; i < 3 ; i++ ) {
	    think();
		SW(numAllowedToEat);
		SW(forks[id]);
		SW(forks[(id+1)];
		Eat();
		SS(forks[id]);
		SS(forks[(id+1)%5]);
		SS(numAllowedToEat);
	}
	think();
}

```

## Actor

http://www.jakubkorab.net/2011/01/why-i-dig-scala-concurrency-and-the-dining-philosophers.html

https://gist.github.com/egonSchiele/5573023

```
require 'rubygems'
require 'celluloid'
 
class Waiter
  include Celluloid
  FORK_FREE = 0
  FORK_USED = 1
  attr_reader :philosophers
  attr_reader :forks
  attr_reader :eating
 
  def initialize(forks)
    @philosophers = []
    @eating = []
    @forks = Array.new(forks, FORK_FREE)
  end
 
  def welcome(philosopher)
    @philosophers << philosopher
    philosopher.async.think
  end
 
  def hungry(philosopher)
    pos = @philosophers.index(philosopher)
 
    left_pos = pos
    right_pos = (pos + 1) % @forks.size
    if @forks[left_pos] == FORK_FREE && @forks[right_pos] == FORK_FREE
      @forks[left_pos] = FORK_USED
      @forks[right_pos] = FORK_USED
      @eating << philosopher
      philosopher.async.eat
    else
      # it's not your turn, keep thinking
      philosopher.async.think
    end
  end
 
  def drop_forks(philosopher)
    pos = @philosophers.index(philosopher)
    left_pos = pos
    right_pos = (pos + 1) % @forks.size
    @forks[left_pos] = FORK_FREE
    @forks[right_pos] = FORK_FREE
    @eating -= [philosopher]
    philosopher.async.think
  end
end
 
class Philosopher
  include Celluloid
  attr_reader :name
  attr_reader :waiter
 
  def initialize(name, waiter)
    @name = name
    @waiter = waiter
    waiter.async.welcome(Actor.current)
  end
 
  def think
    puts "#{name} is thinking"
    sleep(rand)
    puts "#{name} gets hungry"
    waiter.async.hungry(Actor.current)
  end
 
  def eat
    puts "#{name} is eating"
    sleep(rand)
    puts "#{name} burps"
    waiter.async.drop_forks(Actor.current)
  end
end
 
names = %w{Heraclitus Aristotle Epictetus Schopenhauer Popper}
waiter = Waiter.new(names.size)
philosophers = names.map {|name| Philosopher.new(name, waiter)}
 
# The main thread is done! Sleep forever
sleep
```

## Software Transactional Memory

http://adit.io/posts/2013-05-15-Locks,-Actors,-And-STM-In-Pictures.html


---

# Reference

## Wikipedia

http://en.wikipedia.org/wiki/Dining_philosophers_problem

## Semaphore

http://en.wikipedia.org/wiki/Semaphore_(programming)