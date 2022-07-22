# LatestVersion
<span id="noticestart">ChangeLog:
3.11版本更正了声援板中异属性SR经验值为8960。
使用免费空间替代github的功能，替换了所有github相关代码
在其它数据模块新增了衣服推荐项
3.10及之前的版本不再提供远程数据支持
3.12版本更改整体配色方案，新版本整体颜色较旧版本偏亮
调整部分表格布局，使其垂直居中
略调整了悬浮文字位置
支持不同版本对应推送不同的远程数据
修复3.11版本点击下拉菜单可能导致程序闪退的BUG
</span><span id="noticeend"></span>
scrollingMarqueestart 远程空间无法访问，请刷新重试！ scrollingMarqueeend
//remotestart
//格式化时间字符串，值为格林尼治标准时间: YYYYMMDDhhmm
utc_remote=new Date().toISOString().replace(/-|T|:/g,'').slice(0,12);
//发布最新版本，低于该版本所有用户将收到铃铛图标更新提示，请至少保留一个Notice的定义，否则3.12版本会产生报错。
newVersion='3.16';
Notice=''; 
//发现新版本后于铃铛图标后出现气泡图标，鼠标指向该图标出现changelog提示
changelog='v3.16  2022/07/03  @卑微小萌新\n规避了远程空间供应商注入广告及篡改404页面可能导致程序报错的问题\n重新启动github数据做为备用方案\n衣服推荐项的下拉菜单添加了背景颜色，备注的默认值循环显示不同的“小贴士”';
//若使用的程序为最新版本，则在条件时间段内出现一个橙红色气泡提示，鼠标指向出现Notice提示。3.13之后的版本用滚动字幕替代该功能。
if(utc_remote>='202206210000' && utc_remote<'202206211600') { Notice='小提示:\n回忆风车明天凌晨三点到期，\n没送的抓紧送掉了！' } else { Notice='' };
//在条件时间段出现滚动字幕提示
if(utc_remote>='202206270000' && utc_remote<'202206271500') { scrollingMarquee='<font color="red"><b>注意</b>：本次活动今天<b>23点</b>即将到期，分没刷够的或顶油还没送的需要抓紧时间了！</font>'; };
//固定时间出现滚动字幕提示
if(utc_remote.slice(6,8)=='02'){scrollingMarquee=scrollingMarquee+'&nbsp;&nbsp;&nbsp;&nbsp;<font color=""><b>提示</b>：家具商店的VIP币已更新！</font>';};
if(utc_remote.slice(5,6)%2==0 && utc_remote.slice(6,8)=='01'){scrollingMarquee=scrollingMarquee+'&nbsp;&nbsp;&nbsp;&nbsp;<font color=""><b>提示</b>：月票辅助券即将过期！</font>';};
if(new Date().getDay()==1) {scrollingMarquee=scrollingMarquee+'&nbsp;&nbsp;&nbsp;&nbsp;<font color=""><b>提示</b>：活动商店的新常驻扭蛋券已更新！</font>';};
//在web选项插入一条（或几条）有时效性的URL链接
if (document.getElementById('remoteweburl') && utc_remote<202206230000) {document.getElementById('remoteweburl').innerHTML="活动介绍: <a href='#' rel='external nofollow' onclick='useDefBrowser(\"https://tieba.baidu.com/p/7889790615\")'>https://tieba.baidu.com/p/7889790615</a><br><br>"};
//在其它数据最后部分添加一项
if(newVersion=='3.14') {
    if(version==newVersion) { remoteOption='ChangeLog'; } else { remoteOption='更新提示'; }
    remoteText='<br>'+
    'v3.13; 2022/06/21; @卑微小萌新;<br>'+
    '首页增加了滚动字幕提示<br>'+
    '微调了格式<br>'+
    'runRemoteData函数的功能多余且使用受限，应逐步被替代<br><br>'+
    'v3.14; 2022/06/25; @卑微小萌新;<br>'+
    '修正了霞的饰品错误<br>'+
    '现在程序支持运行本地文本文件的代码(文本文件需命名为doaxtools.txt)<br>'+
    '提供doaxtools.txt的示例文件下载<br>'+
    '用户自定义代码建议写入doaxtools.txt中（非是必须如此，只是考虑每次程序更新用户都需要重新粘贴自己的数据而设计的折中方案）<br>'+
    '为匹配程序的charset="gb2312"，doaxtools.txt应保存为ANSI格式，否则将读取到乱码，导致程序报错。<br>'+
    '请修改“myDocuments=\'\'”为你需要放置doaxtools.txt文件的实际路径  <br>'+
    'myDocuments的路径格式举例： <br>'+
    '若将doaxtools.txt放在桌面，则：myDocuments=\'C:\\\\Users\\\\xxx\\\\Desktop\'<br>'+
    '若将doaxtools.txt放在和程序同目录，则；myDocuments=\'.\'<br>'+
    '若将doaxtools.txt放在我的文档根目录则无需修改myDocuments<br>'+
    '若你看不懂上述内容请直接无视之！不影响程序的使用！'
    if(version==newVersion && utc_remote<202206270000) { addOtherData(remoteOption,remoteText);resizeFont(17); };
    if(checkNewVersion(newVersion)) { addOtherData(remoteOption,remoteText);resizeFont(17); };
}
//远程更改表格数据，发现3.16(含)之前的版本四处错误，将在下个版本更正。
if(checkNewVersion('3.17')) {
    document.getElementById("plateTable").rows[4].cells[1].innerHTML="134400";
    document.getElementById("keyTable").rows[7].cells[4].innerHTML="12%-2&#128273;<br>20000pt";
    document.getElementById("keyTable").rows[7].cells[5].innerHTML="15%-2&#128273;<br>20000pt";
    document.getElementById("keyTable").rows[7].cells[8].innerHTML="1.88%";
};
//远程将新女孩添加到女孩属性和涂油提升部分，举例：若新女孩出现在2.1版本发布后，则所有已发布版本理应全部远程添加该女孩，checkNewVersion('2.2')匹配2.2之前的版本，不包含2.2
if(checkNewVersion('2.2')) {
girlAttArrbk=girlAttArr;
girlAttArr = [
['new1','新女孩1',     920,1060,1040,10, '节体F'  ,'假动作F','心理战C','tec','1/3'   ],
['new2','新女孩2',     920,1060,1040,10, '节体F'  ,'假动作F','心理战C','tec','1/4'   ],
['new3','新女孩3',     1060,920,1040,10, '节体F'  ,'杀球F','强压C','pow','1/5'   ],
['new4','新女孩4',     920,1060,1040,10, '节体F'  ,'假动作F','心理战C','tec','1/6'   ]
]
addOilSelect();
createGirlAttTab('tec');
createGirlAttTab('pow');
createGirlAttTab('stm');
girlAttArr=girlAttArrbk.concat(girlAttArr);
altRows('powTable','powevenrowcolor','powoddrowcolor');
altRows('tecTable','tecevenrowcolor','tecoddrowcolor');
altRows('stmTable','stmevenrowcolor','stmoddrowcolor');
};
//排位档期
qualifying_starttime='202206090930'
qualifying_endtime='202206160000'
qualifying_title='2022/06/09“珠宝之夜的愿望～羁绊挑战赛篇～”'
qualifying_notice='点击前往百度贴吧【22.06.09魅力排位】全记录'
qualifying_link='https://tieba.baidu.com/p/7872576277'
if(utc_remote>=qualifying_starttime && utc_remote<qualifying_endtime) {
    if(!checkNewVersion('3.14')) {
        rankArr=[
            ['排名','排名奖励(1-1000)','排名','排名奖励(1001-10000)'],
            ['紫票','月票','常驻券','VIP币','&nbsp;水&nbsp;','紫票','月票','常驻券','VIP币','&nbsp;水&nbsp;'],
            ['1-3',     '20','2',  '0',  '70','15','1001-1500','20','0','7/8','20','7'],
            ['4-10',    '20','1',  '6/8','70','14','1501-2000','20','0','6/8','20','6'],
            ['11-50',   '20','1',  '5/8','60','13','2001-3000','20','0','5/8','10','5'],
            ['51-100',  '20','1',  '3/8','50','12','3001-4000','20','0','4/8','10','4'],
            ['101-200', '20','1',  '3/8','40','11','4001-4500','20','0','3/8','10','4'],
            ['201-400', '20','1',  '2/8','40','10','4501-5000','20','0','3/8','10','3'],
            ['401-500', '20','1',  '2/8','30','9', '5001-6500','20','0','2/8','5', '3'],
            ['501-600', '20','6/8','4/8','30','9', '6501-7000','4', '0','2/8','0', '3'],
            ['601-700', '20','5/8','4/8','30','8', '7001-8000','3', '0','1/8','0', '2'],
            ['701-800', '20','4/8','5/8','30','8', '8001-9000','2', '0','1/8','0', '2'],
            ['801-1000','20','2/8','7/8','20','7', '9001-10000','1','0','1/8','0', '1']
        ]
        addOtherData('排位奖励','<br>',rankArr);resizeFont(10,'text');tableRowSpan(0,0,1);tableColSpan(0,1,4);tableRowSpan(0,2,1);tableColSpan(0,3,4);tableFontWeight();tableFontWeight(2,0);tableFontWeight(3,0);tableFontWeight(4,0);tableFontWeight(5,0);tableFontWeight(7,0);tableFontWeight(11,0);tableFontWeight(3,6);tableFontWeight(7,6);tableFontWeight(8,6);
    }
    qualifying_text='<br><br><br><p style="text-align:center;">'+qualifying_title+'<a title='+qualifying_notice+' style="text-decoration:none;color:blue" href="#" rel="external nofollow" onclick="useDefBrowser(qualifying_link)">分数线</a>(截止23:00)</p>'
    qualifying_table=[['&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;','&nbsp;&nbsp;&nbsp;&nbsp;100&nbsp;&nbsp;&nbsp;&nbsp;','&nbsp;&nbsp;&nbsp;&nbsp;400&nbsp;&nbsp;&nbsp;&nbsp;','&nbsp;&nbsp;&nbsp;&nbsp;800&nbsp;&nbsp;&nbsp;&nbsp;','&nbsp;&nbsp;&nbsp;&nbsp;2000&nbsp;&nbsp;&nbsp;&nbsp;','&nbsp;&nbsp;&nbsp;&nbsp;5000&nbsp;&nbsp;&nbsp;&nbsp;','&nbsp;&nbsp;&nbsp;&nbsp;6500&nbsp;&nbsp;&nbsp;&nbsp;'],
        ['周四','','','','','',''],
        ['周五','','','','','',''],
        ['周六','','','','','',''],
        ['周日','','','','','',''],
        ['周一','','','','','',''],
        ['周二','','','','','',''],
        ['周三','','','','','','']
    ]
    addOtherData('排位分数',qualifying_text,qualifying_table);resizeFont(10.7,'table');tableFontWeight();tableFontWeight('',0);
}
//pvp公式
if(utc_remote<'202206271500') {
    pvpText='<br><br><br>'+
    '<b>屁屁咚魅力</b>=(女神力APL+衣服APL*0.05)*(1+魅力潜力百分比)<br><br>'+
    '<b>屁屁咚力</b></>={3种属性面板*(1+该潜力百分比加成)总和}*(1+0.002*屁屁咚魅力)<br><br>'+
    '注：该属性面板包括人物基础+衣服+流行加成+油<br><br><br>'+
    '————以上数据来自“熊大”大佬！';
    addOtherData('pvp公式',pvpText);resizeFont(17);
}
//女孩生日当天更换背景图片
utc_birthday=utc_remote.slice(4);
if(utc_birthday>='07061600' && utc_birthday<'07071600') {
    document.getElementById('firstDiv').style.backgroundImage = "url(http://doax.freevar.com/img/misaki_birthday.jpg)";
    document.getElementById('firstDiv').style.backgroundSize = "auto";
}
if(utc_birthday>='07301600' && utc_birthday<'07311600') {
    document.getElementById('firstDiv').style.backgroundImage = "url(http://doax.freevar.com/img/patty_birthday.jpg)";
    document.getElementById('firstDiv').style.backgroundSize = "auto";
}
if(utc_birthday>='08041600' && utc_birthday<'08051600') {
    document.getElementById('firstDiv').style.backgroundImage = "url(http://doax.freevar.com/img/ayane_birthday.jpg)";
    document.getElementById('firstDiv').style.backgroundSize = "auto";
}
if(utc_birthday>='08181600' && utc_birthday<'08191600') {
    document.getElementById('firstDiv').style.backgroundImage = "url(http://doax.freevar.com/img/tamaki_birthday.jpg)";
    document.getElementById('firstDiv').style.backgroundSize = "auto";
}
if(utc_birthday>='09141600' && utc_birthday<'09151600') {
    document.getElementById('firstDiv').style.backgroundImage = "url(http://doax.freevar.com/img/kanna_birthday.jpg)";
    document.getElementById('firstDiv').style.backgroundSize = "auto";
}
if(utc_birthday>='09191600' && utc_birthday<'09201600') {
    document.getElementById('firstDiv').style.backgroundImage = "url(http://doax.freevar.com/img/momiji_birthday.jpg)";
    document.getElementById('firstDiv').style.backgroundSize = "auto";
}
if(utc_birthday>='10141600' && utc_birthday<'10151600') {
    document.getElementById('firstDiv').style.backgroundImage = "url(http://doax.freevar.com/img/luna_birthday.jpg)";
    document.getElementById('firstDiv').style.backgroundSize = "auto";
}
if(utc_birthday>='10231600' && utc_birthday<'10241600') {
    document.getElementById('firstDiv').style.backgroundImage = "url(http://doax.freevar.com/img/tsukushi_birthday.jpg)";
    document.getElementById('firstDiv').style.backgroundSize = "auto";
}
//remoteend
