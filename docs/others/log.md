---
counter: True
comment: True
---

# 鱼龙混杂hhh

!!! abstract
    上半年的工具总结，并且制作了一些花模板，算是生活的一些footnote吧

    认识新的工具最开始会有一个不适应期，可以做做这种文档，来确定自己到底走到哪一步。到后来慢慢就能直接适应！


## 神秘资源
<div class="card file-block" markdown="1">
<div class="file-icon"><img src="../../assets/images/pdf.svg" style="height: 3em;"></div>
<div class="file-body">
<div class="file-title">工具记录</div>
<div class="file-meta">8.2 MB / 19 P / 2025-12-31</div>
</div>
<a class="down-button" target="_blank" href="../../assets/files/Ac_Log (1).pdf" markdown="1">:fontawesome-solid-download: 下载</a>
</div>

## 样式文件代码(.sty)
```
\NeedsTeXFormat{LaTeX2e}
\ProvidesPackage{workingonon}[2026/03/17 V1.0 Ac Life OS Package]

% ======================================================
% 1. 核心宏包
% ======================================================
\RequirePackage{xeCJK}
\RequirePackage{geometry}
\RequirePackage{tcolorbox} 
\RequirePackage{titlesec}
\RequirePackage{fancyhdr}
\RequirePackage{enumitem}
\RequirePackage{xcolor}
\RequirePackage{hyperref}
\RequirePackage{amssymb}

% ======================================================
% 2. 页面与字体设置
% ======================================================
\geometry{left=2.5cm, right=2.5cm, top=3cm, bottom=3cm}
\setCJKmainfont{SimSun} % 建议换成思源宋体

% ======================================================
% 3. 颜色定义与背景色
% ======================================================
\definecolor{MyBlue}{RGB}{30, 80, 160}
\definecolor{UpdateGray}{RGB}{245, 211, 255}
\definecolor{Updatepink}{RGB}{255,240,245}
\definecolor{UpdateLightBlue}{RGB}{240, 248, 255}
\definecolor{UpdateFrameBlue}{RGB}{16, 218, 255}
\definecolor{Framegreen}{RGB}{73, 255, 232}
\definecolor{mygreen}{RGB}{144, 255, 167}
\definecolor{cream}{RGB}{250,245,238}
\definecolor{mypurple}{RGB}{237, 179, 255}
\pagecolor{cream} % 全局护眼背景色

% ======================================================
% 4. 自定义环境：更新日志框与论述框
% ======================================================
\newtcolorbox{flowing}[1]{
    colback=UpdateGray,
    colframe=mypurple,
    fonttitle=\bfseries,
    title=随想与工具论述：#1,
    arc=2pt,
    outer arc=2pt,
    boxrule=0.5pt
}

\newtcolorbox{sum4}[1]{
    colback=UpdateGray,
    colframe=mypurple,
    fonttitle=\bfseries,
    title=总结：#1,
    arc=2pt,
    outer arc=2pt,
    boxrule=0.5pt
}

\newtcolorbox{updatelog}[1]{
    colback=Updatepink,
    colframe=pink!60,
    fonttitle=\bfseries,
    title=迭代日志：#1,
    arc=2pt,
    outer arc=2pt,
    boxrule=0.5pt
}

\newtcolorbox{sum3}[1]{
    colback=Updatepink,
    colframe=pink!60,
    fonttitle=\bfseries,
    title=总结：#1,
    arc=2pt,
    outer arc=2pt,
    boxrule=0.5pt
}

\newtcolorbox{dododo}[1]{
    colback=UpdateLightBlue,  
    colframe=UpdateFrameBlue, 
    fonttitle=\bfseries,
    title=全力以赴: #1,
    arc=2pt,
    outer arc=2pt,
    boxrule=0.5pt
}

\newtcolorbox{sum1}[1]{
    colback=UpdateLightBlue,  
    colframe=UpdateFrameBlue, 
    fonttitle=\bfseries,
    title=总结: #1,
    arc=2pt,
    outer arc=2pt,
    boxrule=0.5pt
}

\newtcolorbox{inspiration}[1]{
    colback=mygreen,  
    colframe=Framegreen, 
    fonttitle=\bfseries,
    title=Ling光乍现: #1,
    arc=2pt,
    outer arc=2pt,
    boxrule=0.5pt
}

\newtcolorbox{sum2}[1]{
    colback=mygreen,  
    colframe=Framegreen, 
    fonttitle=\bfseries,
    title=总结: #1,
    arc=2pt,
    outer arc=2pt,
    boxrule=0.5pt
}

% ======================================================
% 5. 页眉页脚设置
% ======================================================
\pagestyle{fancy}
\fancyhf{}
\fancyhead[L]{\small \color{gray} Ac's Workflow \& Life Log}
\fancyhead[R]{\small \color{gray} \leftmark}
\fancyfoot[C]{\thepage}

\endinput
```
