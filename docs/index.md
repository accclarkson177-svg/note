---
hide:
    - date
home: true
template: home.html
statistics: true
---
<div markdown="1" style="max-width: 650px;">

!!! gaia-red "self info"
    这里是AC的个人笔记本哦！

    如果发现了有内容错误可以通过文末评论告诉我吗qwq，我准备做个文末评论区什么的。

    大概是随时更新，~~随时尽显锋芒，用热情想一出是一出~~

??? question "about(site.author)"
    07年生（也有可能是1907年），就读于浙江大学竺可桢学院混合班，爱好是乒乓球，很喜欢玩器材。同时也是竺可桢学院灵韵交响乐团的一个小提琴手，喜欢吃肉，偶尔练琴，欢迎交个朋友组组重奏什么的。

    - 个人导航：https://acxikaly.top
    - 主页：尚在搭建中
    - 微信公众号：Ac轴上的曹点
    - GitHub：https://github.com/accclarkson177-svg
    - bilibili：https://space.bilibili.com/649713675?spm_id_from=333.1007.0.0

??? info "site.statistics"
    页面总数：{{pages}}
    总字数：{{words}}
    代码块行数：{{codes}}
    网站运行时间：<span id="web-time"></span>

</div>


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
        document.getElementById("web-time").innerHTML = y + "<span class=\"heti-spacing\"> </span>年<span class=\"heti-spacing\"> </span>" + d + "<span class=\"heti-spacing\"> </span>天<span class=\"heti-spacing\"> </span>" + h + "<span class=\"heti-spacing\"> </span>小时<span class=\"heti-spacing\"> </span>" + m + "<span class=\"heti-spacing\"> </span>分钟";
    }
    setTimeout(updateTime, 1000 * 60);
}
updateTime();
</script>