---
hide:
    - date
home: true
template: home.html
statistics: true
---
<div markdown="1" style="max-width: 650px; margin-top: -50px; margin-left: 20px;">

# 这是一个精美的封面

[→ 点击查看：关于我](about.md){: .button }

<div markdown="1" style="max-width: 650px;">
!!! gaia-red "self info"
    这里是AC的个人笔记本哦！

    如果发现了有内容错误可以通过文末评论告诉我吗qwq，我准备做个文末评论区什么的。

    大概是随时更新，~~随时尽显锋芒，用热情想一出是一出~~
</div>

??? info "site.statistics"
    页面总数：{{pages}}
    总字数：{{words}}
    代码块行数：{{codes}}
    网站运行时间：<span id="web-time"></span>

```python title="script.py"
if visitor.name == 'Ac':
    print(f"看什么看，快去学习/做视频/写笔记/练琴/{'/'.join(tasks)}\n")
    logging.warning("别摸了")
else:
    print("希望这个小破站点能对你有所帮助ヽ(*´∀｀)八(´∀｀*)ノ\n")
    thanks_list.append(visitor.name)
```

<script>
function updateTime() {
    var date = new Date();
    var now = date.getTime();
    var startDate = new Date("2026/04/13 09:10:00");
    var start = startDate.getTime();
    var diff = now - start;
    var y, d, h, m;
    y = Math.floor(diff / (365 * 24 * 3600 * 1000));
    diff -= y * 365 * 24 * 3600 * 1000;
    d = Math.floor(diff / (24 * 3600 * 1000));
    h = Math.floor(diff / (3600 * 1000) % 24);
    m = Math.floor(diff / (60 * 1000) % 60);
    if (y == 0) {
        document.getElementById("web-time").innerHTML = d + "<span class=\"heti-spacing\"> </span>天<span class=\"heti-spacing\"> </span>" + h + "<span class=\"heti-spacing\"> </span>小时<span class=\"heti-spacing\"> </span>" + m + "<span class=\"heti-spacing\"> </span>分钟";
    } else {
        document.getElementById("web-time").innerHTML = y + "<span class=\"heti-spacing\"> </span>年<span class=\"heti-spacing\"> </span>" + d + "<span class=\"heti-spacing\"> </span>天<span class=\"heti-spacing\"> </span>" + h + "<span class=\"heti-spacing\"> </span>小时";
    }
    setTimeout(updateTime, 1000 * 60);
}
updateTime();
</script>