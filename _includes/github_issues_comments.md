<hr />
<section class="github_issues_comments">
<h2>Comments</h2>
<div>
  Want to leave a comment? Visit <a href="https://github.com/hmybmny/hmybmny.github.io/issues/{{ page.issueid }}" target="_blank"> this post's issue page on GitHub</a> (you'll need a GitHub account.)
</div>
<div id="comments"></div>
<script type="text/javascript">
document.addEventListener("DOMContentLoaded", function(event) {
    function loadComments(data) {
        for (var i=0; i<data.length; i++) {
            var cuser = data[i].user.login;
            var cuserlink = "https://github.com/" + data[i].user.login;
            var clink = "https://github.com/hmybmny/hmybmny.github.io/issues/{{ page.issueid }}#issuecomment-" + data[i].url.substring(data[i].url.lastIndexOf("/")+1);
            var cbody = data[i].body;
            var cavatarlink = data[i].user.avatar_url;
            var options = { year: 'numeric', month: 'short', day: 'numeric' };
            var cdate = new Date(data[i].created_at).toLocaleString("en", options);
            $("#comments").append("<div id='comment'><table><tr><th rowspan='2'><a href=\""+ cuserlink +'\"><img src="' + cavatarlink + '" width="48" height="48">' + "</a></th><td><a href=\""+ cuserlink + "\">" + cuser + "</a> &nbsp; commented on <a href=\"" + clink + "\">" + cdate + "</a></td></tr><tr><td>" + cbody + "</td></tr></table></div>");
        }
    }
    $.ajax("https://api.github.com/repos/hmybmny/hmybmny.github.io/issues/{{ page.issueid }}/comments", {
        headers: {Accept: "application/vnd.github.full+json"},
        cache: false,
        async: false,
        dataType: "json",
        success: function(msg){
        loadComments(msg);
        }
    });
});
</script>
</section>
