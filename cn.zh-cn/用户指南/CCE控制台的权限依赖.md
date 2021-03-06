# CCE控制台的权限依赖<a name="cce_01_0190"></a>

CCE对其他云服务有诸多依赖关系，因此在您开启IAM系统策略授权后，在CCE Console界面中的各项功能需要配置相应的服务权限后才能正常查看或使用，详细说明如下：

>![](public_sys-resources/icon-note.gif) **说明：**   
>-   依赖服务的权限配置均基于您已设置了IAM系统策略授权的CCE FullAccess或CCE ReadOnlyAccess策略权限，详细设置方法请参见[IAM系统策略授权](IAM系统策略授权.md)。  
>-   Tenant Guest权限在你开启IAM系统策略授权之后将不再生效，即无法再进入应用管理、模板市场、插件管理等CCE Console页面，也不会再有全局只读的效果。  
>-   1.11.7-r2及以上版本的集群，显示情况依赖于命名空间权限的设置情况，如果没有设置命名空间权限，则无法查看集群下的资源。  
>    -   如果您设置了全部命名空间的view权限，则可以查看到对应集群的全部命名空间下的资源，但密钥 \( Secret \)除外，密钥 \( Secret \)需要在命名空间权限下设置admin或者edit权限才能查看。  
>    -   如果您设置的是单一命名空间的view权限，则看到的只能是指定命名空间下的资源。  

## 依赖服务的权限设置<a name="section20316111417244"></a>

如果IAM用户需要在CCE Console界面中拥有相应功能的查看或使用权限，请确认已经对该用户所在的用户组设置了CCE FullAccess或CCE ReadOnlyAccess策略的集群权限，再按如下表格增加依赖服务的角色或策略：

**表 1**  CCE Console中依赖服务的角色或策略

<a name="table99001215575"></a>
<table><thead align="left"><tr id="row16901181518712"><th class="cellrowborder" valign="top" width="21.872187218721873%" id="mcps1.2.4.1.1"><p id="p109011015875"><a name="p109011015875"></a><a name="p109011015875"></a>Console界面功能</p>
</th>
<th class="cellrowborder" valign="top" width="28.642864286428644%" id="mcps1.2.4.1.2"><p id="p490115151776"><a name="p490115151776"></a><a name="p490115151776"></a>依赖服务</p>
</th>
<th class="cellrowborder" valign="top" width="49.48494849484948%" id="mcps1.2.4.1.3"><p id="p2090161513711"><a name="p2090161513711"></a><a name="p2090161513711"></a>需配置角色/策略</p>
</th>
</tr>
</thead>
<tbody><tr id="row1090114151176"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p69022151975"><a name="p69022151975"></a><a name="p69022151975"></a>总览</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p119021153716"><a name="p119021153716"></a><a name="p119021153716"></a>应用运维管理 AOM</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p890212155710"><a name="p890212155710"></a><a name="p890212155710"></a>AOM&nbsp;FullAccess（Vision版本为1.0）</p>
</td>
</tr>
<tr id="row159021815871"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p79028151077"><a name="p79028151077"></a><a name="p79028151077"></a>应用管理</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p18902715376"><a name="p18902715376"></a><a name="p18902715376"></a>/</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p290271515712"><a name="p290271515712"></a><a name="p290271515712"></a>当前仅支持主账号、设置了CCE Administrator的子账号或者设置了Tenant Guest的子账号访问。</p>
</td>
</tr>
<tr id="row19902151514719"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p169022151472"><a name="p169022151472"></a><a name="p169022151472"></a>工作负载</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p10902171518718"><a name="p10902171518718"></a><a name="p10902171518718"></a>弹性负载均衡 ELB</p>
<p id="p736818303252"><a name="p736818303252"></a><a name="p736818303252"></a>应用性能管理 APM</p>
<p id="p1780716195243"><a name="p1780716195243"></a><a name="p1780716195243"></a>应用运维管理 AOM</p>
<p id="p14431322102415"><a name="p14431322102415"></a><a name="p14431322102415"></a>NAT网关 NAT</p>
<p id="p2597316122815"><a name="p2597316122815"></a><a name="p2597316122815"></a>对象存储服务 OBS</p>
<p id="p117241658182817"><a name="p117241658182817"></a><a name="p117241658182817"></a>弹性文件服务 SFS</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p57471617102017"><a name="p57471617102017"></a><a name="p57471617102017"></a>正常创建工作负载时不依赖其他服务的权限。</p>
<a name="ul8113732182016"></a><a name="ul8113732182016"></a><ul id="ul8113732182016"><li>如果需要创建ELB类型的服务，需要设置ELB Service Administrator和VPC Administrator。</li><li>如果需要使用Java探针，需要设置AOM&nbsp;FullAccess和APM FullAccess。</li><li>如果需要NAT网关类型的服务，需要设置NAT Gateway Administrator。</li><li>如果使用对象存储，需要全局设置OBS Administrator。<div class="note" id="note1215220141518"><a name="note1215220141518"></a><a name="note1215220141518"></a><span class="notetitle"> 说明： </span><div class="notebody"><p id="p0153120121518"><a name="p0153120121518"></a><a name="p0153120121518"></a>由于缓存的存在，对用户、用户组以及企业项目授予OBS相关的RBAC策略后，大概需要等待13分钟RBAC策略才能生效；授予OBS相关的细粒度策略后，大概需要等待5分钟细粒度策略才能生效。</p>
</div></div>
</li><li>如果使用文件存储，需要设置SFS FullAccess。</li></ul>
</td>
</tr>
<tr id="row39021315071"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p8902715071"><a name="p8902715071"></a><a name="p8902715071"></a>集群管理</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p14902111511717"><a name="p14902111511717"></a><a name="p14902111511717"></a>应用运维管理 AOM</p>
<p id="p178879743210"><a name="p178879743210"></a><a name="p178879743210"></a>费用中心 BSS</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><a name="ul772124115296"></a><a name="ul772124115296"></a><ul id="ul772124115296"><li>如果需要弹性扩容权限，需要设置AOM&nbsp;FullAccess。</li><li>如果需要转包周期，需要设置BSS Administrator。</li></ul>
</td>
</tr>
<tr id="row790217151578"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p1790281519714"><a name="p1790281519714"></a><a name="p1790281519714"></a>节点管理</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p129021156718"><a name="p129021156718"></a><a name="p129021156718"></a>/</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p39021151714"><a name="p39021151714"></a><a name="p39021151714"></a>无需其他依赖权限。</p>
</td>
</tr>
<tr id="row1890251514716"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p39021615371"><a name="p39021615371"></a><a name="p39021615371"></a>网络管理</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p1588385973516"><a name="p1588385973516"></a><a name="p1588385973516"></a>弹性负载均衡 ELB</p>
<p id="p19883145923514"><a name="p19883145923514"></a><a name="p19883145923514"></a>NAT网关 NAT</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p052172153518"><a name="p052172153518"></a><a name="p052172153518"></a>正常创建时不依赖其他服务的权限。</p>
<a name="ul5525210353"></a><a name="ul5525210353"></a><ul id="ul5525210353"><li>如果需要创建ELB类型的服务，需要设置ELB Service Administrator或者VPC Administrator。</li><li>如果需要NAT网关类型的服务，需要设置NAT Administrator。</li></ul>
</td>
</tr>
<tr id="row14486172213364"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p18487522123612"><a name="p18487522123612"></a><a name="p18487522123612"></a>存储管理</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p116411756133813"><a name="p116411756133813"></a><a name="p116411756133813"></a>对象存储服务 OBS</p>
<p id="p126411556163811"><a name="p126411556163811"></a><a name="p126411556163811"></a>弹性文件服务 SFS</p>
<p id="p344642920405"><a name="p344642920405"></a><a name="p344642920405"></a>极速文件存储 EFS（SFS Turbo）</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><a name="ul146023714385"></a><a name="ul146023714385"></a><ul id="ul146023714385"><li>如果使用对象存储，需要全局设置OBS Administrator。<div class="note" id="note927810178150"><a name="note927810178150"></a><a name="note927810178150"></a><span class="notetitle"> 说明： </span><div class="notebody"><p id="p8278617181514"><a name="p8278617181514"></a><a name="p8278617181514"></a>由于缓存的存在，对用户、用户组以及企业项目授予OBS相关的RBAC策略后，大概需要等待13分钟RBAC策略才能生效；授予OBS相关的细粒度策略后，大概需要等待5分钟细粒度策略才能生效。</p>
</div></div>
</li><li>如果使用文件存储，需要设置SFS Administrator。</li><li>如果使用极速文件存储，需要设置SFS Turbo Administrator</li></ul>
</td>
</tr>
<tr id="row1488112216362"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p144881022123614"><a name="p144881022123614"></a><a name="p144881022123614"></a>命名空间</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p64880224363"><a name="p64880224363"></a><a name="p64880224363"></a>/</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p1548818222361"><a name="p1548818222361"></a><a name="p1548818222361"></a>无需其他依赖权限。</p>
</td>
</tr>
<tr id="row748852253612"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p948882214364"><a name="p948882214364"></a><a name="p948882214364"></a>模板市场</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p257594214394"><a name="p257594214394"></a><a name="p257594214394"></a>/</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p1457514212392"><a name="p1457514212392"></a><a name="p1457514212392"></a>当前仅支持主账号、设置了CCE Administrator的子账号或者设置了Tenant Guest的子账号访问。</p>
</td>
</tr>
<tr id="row248812273618"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p10488142233620"><a name="p10488142233620"></a><a name="p10488142233620"></a>插件管理</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p51171157173918"><a name="p51171157173918"></a><a name="p51171157173918"></a>/</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p91181857123912"><a name="p91181857123912"></a><a name="p91181857123912"></a>当前仅支持主账号、设置了CCE Administrator的子账号或者设置了Tenant Guest的子账号访问。</p>
</td>
</tr>
<tr id="row54891622173617"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p1748919220362"><a name="p1748919220362"></a><a name="p1748919220362"></a>权限管理</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p1214191764016"><a name="p1214191764016"></a><a name="p1214191764016"></a>/</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p19141141744012"><a name="p19141141744012"></a><a name="p19141141744012"></a>当前仅支持主账号和设置了CCE Administrator且Security Administrator（全局级策略）的子账号访问。</p>
</td>
</tr>
<tr id="row1588069154010"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p1388110934011"><a name="p1388110934011"></a><a name="p1388110934011"></a>配置中心</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p28816914409"><a name="p28816914409"></a><a name="p28816914409"></a>/</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><a name="ul858844185010"></a><a name="ul858844185010"></a><ul id="ul858844185010"><li>配置项 ( ConfigMap )无需其他依赖权限。</li><li>密钥 ( Secret )需要在命名空间权限下设置admin或者edit权限才能查看。</li></ul>
</td>
</tr>
<tr id="row1090217151179"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p18903615977"><a name="p18903615977"></a><a name="p18903615977"></a>帮助中心</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p943035294110"><a name="p943035294110"></a><a name="p943035294110"></a>/</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p1343065219410"><a name="p1343065219410"></a><a name="p1343065219410"></a>无需其他依赖权限。</p>
</td>
</tr>
<tr id="row1853314583492"><td class="cellrowborder" valign="top" width="21.872187218721873%" headers="mcps1.2.4.1.1 "><p id="p9533958114919"><a name="p9533958114919"></a><a name="p9533958114919"></a>其他服务跳转</p>
</td>
<td class="cellrowborder" valign="top" width="28.642864286428644%" headers="mcps1.2.4.1.2 "><p id="p19533258154918"><a name="p19533258154918"></a><a name="p19533258154918"></a>容器镜像服务 SWR</p>
<p id="p11154184565220"><a name="p11154184565220"></a><a name="p11154184565220"></a>应用服务网格 ASM</p>
<p id="p4509331523"><a name="p4509331523"></a><a name="p4509331523"></a>应用运维管理 AOM</p>
<p id="p581510413526"><a name="p581510413526"></a><a name="p581510413526"></a>多云容器平台 MCP</p>
<p id="p458184745311"><a name="p458184745311"></a><a name="p458184745311"></a>云监控服务 Cloud Eye（存储管理与节点管理的<span class="uicontrol" id="uicontrol11578121711418"><a name="uicontrol11578121711418"></a><a name="uicontrol11578121711418"></a>“监控”</span>跳转）</p>
</td>
<td class="cellrowborder" valign="top" width="49.48494849484948%" headers="mcps1.2.4.1.3 "><p id="p253325815496"><a name="p253325815496"></a><a name="p253325815496"></a>为便于您快速进入CCE相关服务的控制台，在<a href="https://console.huaweicloud.com/cce2.0/?utm_source=helpcenter" target="_blank" rel="noopener noreferrer">CCE控制台</a>中增加了其他服务的跳转链接，CCE默认没有这些服务的全部权限，如果IAM用户需要查看或使用其功能，请按照该服务的权限策略说明设置相应的权限策略。</p>
</td>
</tr>
</tbody>
</table>

## 示例流程<a name="section129815361135"></a>

本章节通过为IAM用户“James”增加CCE**“总览“**页面监控信息的查看权限为例进行演示。

IAM用户“James”在用户组“开发人员组”，“开发人员组”仅有CCE ReadOnlyAccess权限。而参照[表1](#table99001215575)可知，CCE总览页面的监控信息还需要增加“AOM FullAccess”策略才能正常查看。

**图 1**  依赖服务授权流程<a name="fig3687142183218"></a>  
![](figures/依赖服务授权流程.png "依赖服务授权流程")

## 步骤一：验证用户当前权限<a name="section330722611126"></a>

1.  使用IAM用户“James”登录[CCE控制台](https://console.huaweicloud.com/cce2.0/?utm_source=helpcenter)，IAM用户登录方式请参见[步骤三：使用IAM用户登录并验证权限](IAM系统策略授权.md#section1953761017615)。
2.  单击左侧导航栏中的“总览“，进入总览页面，可以看到该用户无权查看监控相关的模块信息。

    **图 2**  无权查看监控信息<a name="fig1825716752613"></a>  
    ![](figures/无权查看监控信息.png "无权查看监控信息")


## 步骤二：为用户组增加系统策略<a name="section10561192612817"></a>

1.  IAM用户“James”退出登录，使用主账号登录[CCE控制台](https://console.huaweicloud.com/cce2.0/?utm_source=helpcenter)。
2.  在CCE控制台中，单击左侧导航栏中的“权限管理“，在“集群权限“页签中单击“开发人员组”后的“设置权限“。

    **图 3**  设置用户组权限<a name="fig1511051633412"></a>  
    ![](figures/设置用户组权限.png "设置用户组权限")

3.  在弹出的“设置权限“窗口中，单击“去设置“。

    **图 4**  设置权限<a name="fig234120192369"></a>  
    ![](figures/设置权限.png "设置权限")

4.  进入统一身份认证服务的“用户组 \> 开发人员组“页面，在“用户组权限“页签中，单击“配置权限“。

    **图 5**  设置用户组策略<a name="fig612134716411"></a>  
    ![](figures/设置用户组策略.png "设置用户组策略")

5.  在弹出的“配置权限“窗口中，选择作用范围。此处选择“区域级项目“，并在下拉框中选择需要授权的区域。

    **图 6**  选择作用范围<a name="fig816544065514"></a>  
    ![](figures/选择作用范围.png "选择作用范围")

6.  在权限列表上方的搜索框中搜索“AOM“，单击“AOM FullAccess“策略并选中，单击“确定“。

    **图 7**  添加AOM FullAccess策略<a name="fig12111191814494"></a>  
    ![](figures/添加AOM-FullAccess策略.png "添加AOM-FullAccess策略")

7.  在“权限管理“页签中可以看到已经增加“AOM FullAccess“策略。

    **图 8**  确认添加策略<a name="fig17730855195315"></a>  
    ![](figures/确认添加策略.png "确认添加策略")

8.  返回[CCE控制台](https://console.huaweicloud.com/cce2.0/?utm_source=helpcenter)，在“权限管理“的“集群权限“页签下单击右上角的刷新图标![](figures/zh-cn_image_0173364181.png)，可以看到“AOM FullAccess“权限策略已添加成功。

    **图 9**  权限策略添加成功<a name="fig4349250117"></a>  
    ![](figures/权限策略添加成功.png "权限策略添加成功")


## 步骤三：验证用户新增权限<a name="section787411356120"></a>

1.  使用IAM用户“James”登录[CCE控制台](https://console.huaweicloud.com/cce2.0/?utm_source=helpcenter)。
2.  单击左侧导航栏中的“总览“，进入总览页面，可以看到该用户已有权查看监控相关的模块信息。

    **图 10**  可正常查看总览页监控信息<a name="fig7651125010199"></a>  
    ![](figures/可正常查看总览页监控信息.png "可正常查看总览页监控信息")

3.  为IAM用户“James”增加查看总览页监控相关的依赖服务权限完成，验证可正常查看。

