https://github.com/nforge/yobi

요거 따라서 잘 나가다가

마지막에 삑사리...

```
[error] C:/play-2.1.0/yobi/app/Global.java:207: illegal start of type
[error]                     return ok(secret.render(SiteAdmin.SITEADMIN_DEFAULT_LOGINID, new Form<>(User.class)));
[error]                                                                                           ^
[error] C:/play-2.1.0/yobi/app/Global.java:207: > expected
[error]                     return ok(secret.render(SiteAdmin.SITEADMIN_DEFAULT_LOGINID, new Form<>(User.class)));
[error]                                                                                                  ^
[error] C:/play-2.1.0/yobi/app/Global.java:207: <identifier> expected
[error]                     return ok(secret.render(SiteAdmin.SITEADMIN_DEFAULT_LOGINID, new Form<>(User.class)));
[error]                                                                                                       ^
[error] C:/play-2.1.0/yobi/app/Global.java:207: '{' expected
[error]                     return ok(secret.render(SiteAdmin.SITEADMIN_DEFAULT_LOGINID, new Form<>(User.class)));
[error]                                                                                                          ^
[error] C:/play-2.1.0/yobi/app/Global.java:212: ';' expected
[error] ^
[error] C:/play-2.1.0/yobi/app/Global.java:286: '}' expected
[error] ^
[error] C:/play-2.1.0/yobi/app/actors/PostReceiveActor.java:62: illegal start of type
[error]         List<RevCommit> commits = new ArrayList<>();
[error]                                                 ^
[error] C:/play-2.1.0/yobi/app/actors/PostReceiveActor.java:62: > expected
[error]         List<RevCommit> commits = new ArrayList<>();
[error]                                                    ^
[error] C:/play-2.1.0/yobi/app/actors/PostReceiveActor.java:63: illegal start of type
[error]         List<String> refNames = new ArrayList<>();
[error]                                               ^
[error] C:/play-2.1.0/yobi/app/actors/PostReceiveActor.java:63: > expected
[error]         List<String> refNames = new ArrayList<>();
[error]                                                  ^
[error] C:/play-2.1.0/yobi/app/actors/PostReceiveActor.java:102: illegal start of type
[error]         List<ReceiveCommand.Type> allowdTypes = new ArrayList<>();
[error]                                                               ^
[error] C:/play-2.1.0/yobi/app/actors/PostReceiveActor.java:102: > expected
[error]         List<ReceiveCommand.Type> allowdTypes = new ArrayList<>();
[error]                                                                  ^
[error] C:/play-2.1.0/yobi/app/actors/PostReceiveActor.java:111: illegal start of type
[error]         List<RevCommit> list = new ArrayList<>();
[error]                                              ^
[error] C:/play-2.1.0/yobi/app/actors/PostReceiveActor.java:111: > expected
[error]         List<RevCommit> list = new ArrayList<>();
[error]                                                 ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:93: illegal start of type
[error]         Map<String, String> fileInfo = new HashMap<>();
[error]                                                    ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:93: > expected
[error]         Map<String, String> fileInfo = new HashMap<>();
[error]                                                       ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:230: illegal start of type
[error]         Map<String, String> metadata = new HashMap<>();
[error]                                                    ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:230: > expected
[error]         Map<String, String> metadata = new HashMap<>();
[error]                                                       ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:256: illegal start of type
[error]                 new HashMap<>();
[error]                             ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:256: > expected
[error]                 new HashMap<>();
[error]                                ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:259: illegal start of type
[error]         List<Map<String, String>> userFiles = new ArrayList<>();
[error]                                                             ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:259: > expected
[error]         List<Map<String, String>> userFiles = new ArrayList<>();
[error]                                                                ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:271: illegal start of type
[error]             List<Map<String, String>> attachments = new ArrayList<>();
[error]                                                                   ^
[error] C:/play-2.1.0/yobi/app/controllers/AttachmentApp.java:271: > expected
[error]             List<Map<String, String>> attachments = new ArrayList<>();
[error]                                                                      ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:66: illegal start of type
[error]         Form<SearchCondition> postParamForm = new Form<>(SearchCondition.class);
[error]                                                        ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:66: > expected
[error]         Form<SearchCondition> postParamForm = new Form<>(SearchCondition.class);
[error]                                                                          ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:66: <identifier> expected
[error]         Form<SearchCondition> postParamForm = new Form<>(SearchCondition.class);
[error]                                                                               ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:66: '{' expected
[error]         Form<SearchCondition> postParamForm = new Form<>(SearchCondition.class);
[error]                                                                                ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:68: <identifier> expected
[error]         searchCondition.pageNum = pageNum - 1;
[error]                                 ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:69: illegal start of type
[error]         if(searchCondition.orderBy.equals("id")) {
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:73: <identifier> expected
[error]         ExpressionList<Posting> el = searchCondition.asExpressionList(project);
[error]                                                                               ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:77: illegal start of type
[error]         return ok(list.render("menu.board", project, posts, searchCondition, notices));
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:77: <identifier> expected
[error]         return ok(list.render("menu.board", project, posts, searchCondition, notices));
[error]                                                                                       ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:92: ';' expected
[error]     public static Result newPostForm(String userName, String projectName) {
[error]                                     ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:98: <identifier> expected
[error]         return ok(create.render("post.new", new Form<>(Posting.class), project, isAllowedToNotice));
[error]                                                                     ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:98: '{' expected
[error]         return ok(create.render("post.new", new Form<>(Posting.class), project, isAllowedToNotice));
[error]                                                                                                    ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:114: ';' expected
[error]     public static Result newPost(String userName, String projectName) {
[error]                                 ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:115: <identifier> expected
[error]         Form<Posting> postForm = new Form<>(Posting.class).bindFromRequest();
[error]                                                          ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:115: '{' expected
[error]         Form<Posting> postForm = new Form<>(Posting.class).bindFromRequest();
[error]                                                                             ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:118: illegal start of type
[error]         if (postForm.hasErrors()) {
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:124: <identifier> expected
[error]         final Posting post = postForm.get();
[error]                                            ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:126: illegal start of type
[error]         if (post.body == null) {
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:130: <identifier> expected
[error]         post.createdDate = JodaDateUtil.now();
[error]                                              ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:131: <identifier> expected
[error]         post.updatedDate = JodaDateUtil.now();
[error]                          ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:132: <identifier> expected
[error]         post.setAuthor(UserApp.currentUser());
[error]                       ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:133: <identifier> expected
[error]         post.project = project;
[error]                      ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:135: <identifier> expected
[error]         post.save();
[error]                  ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:138: <identifier> expected
[error]         Attachment.moveAll(UserApp.currentUser().asResource(), post.asResource());
[error]                           ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:140: <identifier> expected
[error]         NotificationEvent.afterNewPost(post);
[error]                                       ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:142: illegal start of type
[error]         return redirect(routes.BoardApp.post(project.owner, project.name, post.getNumber()));
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:142: <identifier> expected
[error]         return redirect(routes.BoardApp.post(project.owner, project.name, post.getNumber()));
[error]                                                                                             ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:161: ';' expected
[error]     public static Result post(String userName, String projectName, Long number) {
[error]                              ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:173: <identifier> expected
[error]         Form<PostingComment> commentForm = new Form<>(PostingComment.class);
[error]                                                                           ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:173: '{' expected
[error]         Form<PostingComment> commentForm = new Form<>(PostingComment.class);
[error]                                                                            ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:174: illegal start of type
[error]         return ok(view.render(post, commentForm, project));
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:174: <identifier> expected
[error]         return ok(view.render(post, commentForm, project));
[error]                                                           ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:191: ';' expected
[error]     public static Result editPostForm(String owner, String projectName, Long number) {
[error]                                      ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:195: <identifier> expected
[error]         Form<Posting> editForm = new Form<>(Posting.class).fill(posting);
[error]                                                          ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:195: '{' expected
[error]         Form<Posting> editForm = new Form<>(Posting.class).fill(posting);
[error]                                                                         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:198: illegal start of type
[error]         return ok(edit.render("post.modify", editForm, posting, number, project, isAllowedToNotice));
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:198: <identifier> expected
[error]         return ok(edit.render("post.modify", editForm, posting, number, project, isAllowedToNotice));
[error]                                                                                                     ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:216: ';' expected
[error]     public static Result editPost(String userName, String projectName, Long number) {
[error]                                  ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:217: <identifier> expected
[error]         Form<Posting> postForm = new Form<>(Posting.class).bindFromRequest();
[error]                                                          ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:217: '{' expected
[error]         Form<Posting> postForm = new Form<>(Posting.class).bindFromRequest();
[error]                                                                             ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:220: illegal start of type
[error]         if (postForm.hasErrors()) {
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:226: <identifier> expected
[error]         final Posting post = postForm.get();
[error]                                            ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:236: illegal start of type
[error]         return editPosting(original, post, postForm, redirectTo, updatePostingBeforeUpdate);
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:236: <identifier> expected
[error]         return editPosting(original, post, postForm, redirectTo, updatePostingBeforeUpdate);
[error]                                                                                            ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:254: ';' expected
[error]     public static Result deletePost(String owner, String projectName, Long number) {
[error]                                    ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:284: <identifier> expected
[error]         Form<PostingComment> commentForm = new Form<>(PostingComment.class)
[error]                                                                           ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:285: '{' expected
[error]                 .bindFromRequest();
[error]                                   ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:287: illegal start of type
[error]         if (commentForm.hasErrors()) {
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:291: <identifier> expected
[error]         final PostingComment comment = commentForm.get();
[error]                                                         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:293: illegal start of type
[error]         return newComment(comment, commentForm, redirectTo, new Runnable() {
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:298: <identifier> expected
[error]         });
[error]           ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:317: ';' expected
[error]     public static Result deleteComment(String userName, String projectName, Long number, Long commentId) {
[error]                                       ^
[error] C:/play-2.1.0/yobi/app/controllers/BoardApp.java:325: '}' expected
[error] ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeApp.java:93: illegal start of type
[error]         List<ObjectNode> recursiveData = new ArrayList<>();
[error]                                                        ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeApp.java:93: > expected
[error]         List<ObjectNode> recursiveData = new ArrayList<>();
[error]                                                           ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:174: illegal start of type
[error]         Form<CommitComment> codeCommentForm = new Form<>(CommitComment.class)
[error]                                                        ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:174: > expected
[error]         Form<CommitComment> codeCommentForm = new Form<>(CommitComment.class)
[error]                                                                        ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:174: <identifier> expected
[error]         Form<CommitComment> codeCommentForm = new Form<>(CommitComment.class)
[error]                                                                             ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:175: '{' expected
[error]                 .bindFromRequest();
[error]                                   ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:179: illegal start of type
[error]         if (codeCommentForm.hasErrors()) {
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:187: <identifier> expected
[error]         CommitComment codeComment = codeCommentForm.get();
[error]                                                          ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:188: <identifier> expected
[error]         codeComment.project = project;
[error]                             ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:189: <identifier> expected
[error]         codeComment.commitId = commitId;
[error]                              ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:190: <identifier> expected
[error]         codeComment.createdDate = new Date();
[error]                                 ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:191: <identifier> expected
[error]         codeComment.setAuthor(UserApp.currentUser());
[error]                              ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:192: <identifier> expected
[error]         codeComment.save();
[error]                         ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:194: <identifier> expected
[error]         Attachment.moveAll(UserApp.currentUser().asResource(), codeComment.asResource());
[error]                           ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:197: <identifier> expected
[error]         toView = backToThePullRequestCommitView(toView);
[error]                ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:199: <identifier> expected
[error]         NotificationEvent.afterNewCommitComment(project, codeComment, toView.url());
[error]                                                ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:201: illegal start of type
[error]         return redirect(toView + "#comment-" + codeComment.id);
[error]         ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:201: <identifier> expected
[error]         return redirect(toView + "#comment-" + codeComment.id);
[error]                                                               ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:204: illegal start of expression
[error]     private static Call backToThePullRequestCommitView(Call toView) {
[error]     ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:213: ';' expected
[error]     @With(NullProjectCheckAction.class)
[error]                                  ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:213: <identifier> expected
[error]     @With(NullProjectCheckAction.class)
[error]                                       ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:225: '{' expected
[error] }
[error] ^
[error] C:/play-2.1.0/yobi/app/controllers/CodeHistoryApp.java:226: '}' expected
[error] ^
[error] 100 errors
[error] (compile:compile) javac returned nonzero exit code
[error] application -

! @6h24n31g3 - Internal server error, for (GET) [/] ->

sbt.PlayExceptions$CompilationException: Compilation error[illegal start of type]
        at sbt.PlayReloader$$anon$2$$anonfun$reload$2$$anonfun$apply$15$$anonfun$apply$16.apply(PlayReloader.scala:349) ~[na:na]
        at sbt.PlayReloader$$anon$2$$anonfun$reload$2$$anonfun$apply$15$$anonfun$apply$16.apply(PlayReloader.scala:349) ~[na:na]
        at scala.Option.map(Option.scala:133) ~[scala-library.jar:na]
        at sbt.PlayReloader$$anon$2$$anonfun$reload$2$$anonfun$apply$15.apply(PlayReloader.scala:349) ~[na:na]
        at sbt.PlayReloader$$anon$2$$anonfun$reload$2$$anonfun$apply$15.apply(PlayReloader.scala:346) ~[na:na]
        at scala.Option.map(Option.scala:133) ~[scala-library.jar:na]
[warn] play - No application found at invoker init
```

ㅠㅅㅠ