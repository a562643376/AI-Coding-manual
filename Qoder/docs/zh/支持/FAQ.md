> ## Documentation Index
> Fetch the complete documentation index at: https://docs.qoder.com/llms.txt
> Use this file to discover all available pages before exploring further.

# FAQ

本常见问题解答覆盖与 Qoder 相关的常见疑问，包括安装、登录、支持的平台、语言兼容性、数据安全、计费、网络问题与故障排查。

如果遇到问题，请先尝试重启 Qoder。若仍未解决，请通过 [contact@qoder.com](mailto:contact@qoder.com) 联系我们，我们的支持团队将尽快协助你。

<div id="getting-started">
  ## 快速入门
</div>

<div id="what-should-i-do-if-qoder-is-stuck-on-qoder-starting">
  ### 如果 Qoder 一直停在“Qoder starting”，我该怎么办？
</div>

请尝试以下步骤：

1. 检查你的环境。 a. 确保 Qoder 已更新到最新版本。 b. 确认你的操作系统和系统架构支持 Qoder。
2. 测试网络连接。

a. 在终端运行以下命令以检查连通性。如果收到 `pong`，表示网络已连接。否则，请检查防火墙，或请你的 IT 管理员将以下域名加入白名单。

```bash  theme={null}
curl https://{hosts}/algo/api/v1/ping 

// 您可以将 {hosts} 替换为以下任一选项：
1. api1.qoder.sh
2. api2.qoder.sh
3. api3.qoder.sh
```

b. 如需使用代理，请按以下格式设置代理地址：

```plaintext  theme={null}
http(s)://用户名:密码@代理服务器地址:端口
```

c. 清理 DNS 缓存：

* Windows：`ipconfig /flushdns`。
* macOS：`sudo killall -HUP mDNSResponder`。

1. 清理本地缓存。
   a. 结束 Qoder 进程。
   b. 删除 `.Qoder` 目录：

* Windows：
  * `C:\Users\[username]\.Qoder`
  * C:\Users\Username\AppData\Local\Programs\Qoder\\

```text  theme={null}
Windows: 
C:\Users\[username]\.Qoder
C:\Users\Username\AppData\Local\Programs\Qoder\

macOS: 
/Applications/Qoder.app
```

c. 重启 Qoder。

1. 如果问题仍然存在，手动启动：
   a. 前往目录：`.Qoder/bin/x.x.x/CPU_architecture_64_system/`
   ```text  theme={null}
   Windows：C:\Users\Username\AppData\Local\Programs\Qoder\resources\app\resources\bin$version`CPU_architecture_64_system`\Qoder.exe
   Mac：/Applications/Qoder.app/Contents/Resources/app/resources\bin$versionCPU_ahicture_64_system\Qoder 
   ```
   b. 运行：
   ```bash  theme={null}
   Qoder.exe start 或 Qoder start
   ```
   c. 再次尝试登录。
2. （可选）排查安全相关问题
   a. 如果你看到“不兼容的程序”消息或 Qoder 无法启动：
   i. 点击右下角的 Qoder 图标，选择**高级设置**。
   ii. 将解压路径移动到非 C 盘的文件夹（公司可能限制对 C 盘的读写权限），并确保该路径以一个空文件夹结尾。
   iii. 重启 Qoder。
   b. 将 Qoder 添加到防火墙/安全软件的允许列表：
   i. **控制面板** > **系统和安全** > **Windows Defender 防火墙** > **允许的应用**。
   ii. 公司安全软件也可能要求你放行：

```plaintext  theme={null}
Windows：
C:\Users\Username\AppData\Local\Programs\Qoder\resources\app\resources\bin\$version\CPU_architecture_64_system\Qoder.exe
C:\Users\Username\.qoder\bin\qoder.exe

Mac：
/Applications/Qoder.app/Contents/Resources/app/resources\bin\$version\CPU_architecture_64_system\Qoder
```

````text  theme={null}

## 登录和权限

### 如果登录失败或看到权限被拒绝错误怎么办？

- 过期的登录会话需要您重新尝试。
- 确保您的网络允许访问下面列出的域名，并配置代理（如果需要）。详情请参阅 [配置网络代理](https://docs.qoder.com/user-guide/configure-network-proxy)。

```plaintext
api1.qoder.sh
api2.qoder.sh
api3.qoder.sh
````

* 更改设置后，请完全退出 Qoder 并重新启动。

<div id="proxy-and-connectivity">
  ### 代理与连接
</div>

* Qoder 支持 HTTP、HTTPS 和 SOCKS5 代理。请在 Qoder 的设置中进行配置。更多详情参见[配置网络代理](https://docs.qoder.com/user-guide/configure-network-proxy)。
* 要测试连接，请运行：

```powershell  theme={null}
curl https://{hosts}/algo/api/v1/ping 

//您可以将 {hosts} 替换为以下任一选项：
1. api1.qoder.sh
2. api2.qoder.sh
3. api3.qoder.sh
```

如果返回 `pong`，说明你的网络已连接到 Qoder 服务器。

### 遇到网络问题如何排查？

为了更好地帮助你解决问题，请按照以下步骤操作并提供相关信息：

1. 请进入“Qoder设置” > “网络” > 运行诊断，并将完整的诊断结果发送给我们。
2. 你当前是否正在使用 VPN、代理或企业网络？如果是，请尝试关闭这些服务或将网络切换至其他连接。
3. 尝试在聊天界面中选择不同分级的模型，观察响应速度是否有改善。
4. 如果以上操作后问题仍然存在，请进一步提供以下信息以便我们深入调查：
   * 发生延迟的具体示例提示及对应的时间戳；
   * 打开“帮助”>“切换开发者工具”> 查看控制台错误日志并截图发送；
   * 此问题是在所有项目中都出现，还是仅限于某个特定的工作区？
   * 此问题在相同网络下的其他用户是否能复现？
     以上信息通过"问题上报"功能进行反馈。

<div id="account-management">
  ## **帐户管理**
</div>

<div id="my-account-is-suspended-how-can-i-reactivate-it">
  ### **我的账户被暂停了。如何重新激活？**
</div>

如果你的账户因**创建过多免费试用账户**而被暂停，你可以按照以下步骤重新激活：

1. 登录 [Qoder 官网](https://qoder.com/)，点击右上角头像，进入 **Settings** > **Usage**。
2. 在 Usage 页面顶部找到暂停通知横幅，点击 Reactivate Account。
3. **确认政策提示：** 为防止滥用，我们的政策仅允许你的**首个账户**享受免费 Pro 试用。重新激活将放弃此账户剩余的 Pro Trial Credits（将被清零）。确认后，此账户将自动重新激活并恢复正常使用。

### 我的 Pro 试用为什么被撤销了？

根据我们的服务条款：

* Pro 试用资格（包含 300 Credits 试用额度）仅限每位用户享受一次，注册多个账号获得的试用资格将被撤销。
* 不支持在虚拟机里使用 Pro 试用资格。

因此你的 Pro 试用资格被回收，并向你发送了邮件通知。你仍然可以继续使用 Qoder，如需更多 Credits，请[前往官网](https://qoder.com/pricing)升级订阅计划。

<div id="how-much-does-it-cost">
  ### 如何计费？
</div>

Qoder 提供灵活的价格以满足多样化需求。新用户可享受为期 2 周的 Pro 试用，期间可完整使用所有 Pro 专属功能。

试用结束后，您有以下选项：

* 升级至 Pro 方案
* 升级至 Pro+ 方案，获得相比 Pro 3 倍的 Credits 配额
* 升级至 Ultra 方案，获得相比 Pro 10 倍的 Credits 配额，适合 Agent 重度用户
* 升级至团队或企业版
* 不进行任何操作，将自动降级至我们的免费方案

在 Qoder 中的使用以 Credits 计量。每个付费方案都包含特定数量的 Credits ，便于您选择最符合需求的方案。了解更多详情，请访问我们的 [Pricing](https://qoder.com/pricing) 页面。

请注意，除非另有说明，所有显示的价格均不含适用税费（如增值税或销售税）。最终税额取决于多种因素，包括但不限于您的账单地址或税务登记号。

为确保所有用户都能获得公平的试用体验，Pro 试用每位用户仅限一个账户。任何额外创建的试用账户将被停用。

<div id="how-does-the-pro-trial-work">
  ### 专业版试用如何运作？
</div>

当新用户首次登录 Qoder 客户端，包括 Qoder IDE，CLI，或是 Jetbranis 插件（**需使用最新版本；不支持在虚拟机上运行**）时，将获得一次性的免费 2 周（14 天）专业版试用。试用包含 300 Credits 以及对专业版专属功能的完整访问权限。试用到期后，你的账户将自动降级为免费方案，任何未使用的试用 Credits 将被清空。

如果你在试用结束前升级为付费方案（不包括 Teams 版），剩余的试用 Credits 将自动转换为一个 Credit Pack，并以原有的到期日期保留在你的账户中。这样可确保你不会因提前升级而损失未使用的 Credits 。

为确保公平的试用体验，每位用户的专业版试用仅限一个账户。任何额外创建的试用账户将被停用。

<div id="what-happens-when-my-free-trial-ends">
  ### 试用期结束后会怎样？
</div>

当试用期结束时，你有以下选择：

* 升级到付费方案：选择最符合你需求的订阅，解锁更多资源，参见[价格页](https://qoder.com/pricing)。
* 切换到免费方案：你随时可以使用我们的免费方案，适合轻量使用场景。

<div id="what-happens-if-i-run-out-of-my-credits-during-the-trial">
  ### 试用期间如果我的 Credits 用完了会怎样？
</div>

你可以随时升级到 Pro 、Pro+ 或 Ultra 方案以获取更多 Credits 。如果你选择继续使用 Free 方案，也不用担心——我们会让你在基础模型上继续使用，但会有每日和每月限额。

当使用基础模型时，将会有以下变化：

* 你将切换到基础模型：你仍可继续使用我们的服务，但会有使用限额。
* 性能可能会有所变化：基础模型在处理复杂任务时不如更高阶的模型强大。
* 你可能会注意到 Agent 模式和 Quest 模式等功能的性能差异，尤其是在图像对话质量和整体效果方面。

### 使用过程中触发已达使用上限的提示怎么办？

对于轻量免费模型的使用，我们存在一定日和月度的使用额度限制，对应额度周期刷新。

如果你在使用问答或行间编辑时，触发达到轻量免费模型使用限额的提示，请切换至 Auto 等其他模型类型继续使用。如暂无 Credits，请[升级订阅计划](https://docs.qoder.com/zh/account/pricing)后使用。

## Teams 订阅计划

### 什么是 Teams 订阅计划？

面向组织和团队的使用场景，我们推出了 Teams 订阅计划，包括并不限于以下特性，并在持续演进中：

* 集中支付组织账单
* 集中的管理员控制台，支持强制管理成员访问权限、数据隐私模式等
* 支持账号域限制，非域内账号访问控制
* 支持单点登录（SSO）

详情参见[ Teams 说明](https://docs.qoder.com/zh/account/teams/teams-pricing)。

### 席位包含的 Credits 额度可以组织内共享吗？

席位的 Credits 不可组织内共享。

* 每个席位包含 2000 Credits 配额，席位的额度不支持转移和共享。
* 席位的 Credits 仅在当前订阅周期内有效。订阅周期结束时，未用尽的 Credits 将自动重置为 0。

为解决部分成员订阅周期内额度不足的问题，我们即将上线共享资源包以按需补充额度。

### 我席位的 Credits 额度为什么比别人少？

席位的 Credits 额度与席位购买使用的时间有关。如果在周期中途加入，将根据比例进行计费，同时分配的额度也可能会按比例减少。别担心，下一个周期将恢复为完整额度。

* 对于官网购买的组织，当前周期可用额度取决于所使用席位的购买时间，如果在计费周期中途购买的席位，首个周期费用与可用额度已按周期剩余时间比例分配。你的可用额度将在下一个完整周期更新为标准值。
* 对于云市场兑换的组织，当前周期可用额度取决于你加入组织的时间，如果在计费周期中途加入，首个周期费用与可用额度已按周期剩余时间比例分配。可用额度将在下一个完整周期更新为标准值。

### Teams 版可以开具中国制式的发票吗？

官网购买支持下载购买服务单据，但不支持开中国制式发票。

你可以通过支持开具中国发票的三方渠道购买兑换码，目前 Qoder 已上架并支持[阿里云云市场](https://market.aliyun.com/detail/cmgj00072560.html?spm=5176.730005.result.2.bbb8414aScXLKN\&innerSource=search_qoder#sku=yuncode6656000001)购买。兑换码价值、使用规则和有效期以购买渠道规则为准。

如通过三方渠道购买，请提前咨询对应渠道是否可开具符合要求的发票制式。

三方渠道兑换码购买请[参见说明](https://docs.qoder.com/zh/account/teams/about-redeem)。

### 席位如何计费？

席位按组织内计费角色的人数收费，当计费角色的成员增加时，将立即自动消耗一个席位。若可用的席位数不足，将无法添加计费角色的新成员，此时请手动升配席位数以确保成员能够添加并正常使用。

席位自支付购买日立即开通生效并计算订阅周期，订阅周期结束时到期失效。

参见更多[计费说明](https://docs.qoder.com/zh/account/teams/teams-pricing#%E5%B8%AD%E4%BD%8D%E8%AE%A1%E9%87%8F)。

<Tip>
  如果通过兑换码模式创建组织，计费角色成员增加时将自动消耗一个席位月余额。而已经兑换进组织余额的席位月额度有效期 2 年，有效期内均可使用。兑换码兑换的组织余额不跟随订阅周期过期失效。兑换码购买请[参见说明](https://docs.qoder.com/zh/account/teams/about-redeem)。
</Tip>

### 为什么我尝试登录时会收到“加入组织失败”的错误提示？

如果你在登录时遇到 “加入组织失败" 错误，则表示你的企业管理员已将你的电子邮件域关联到 Qoder Teams 组织。此设置旨在自动将该域下的所有账户添加到组织中。但是，由于组织已用完可用席位，因此该过程失败。

要解决此问题，请联系你公司的 IT 管理员，并请他们购买更多席位。席位足够后，请尝试再次登录。届时，你将被自动添加到组织中，并可以开始使用 Teams 订阅计划。

<div id="supported-platforms">
  ## 支持的平台
</div>

* macOS：11.0 及更高版本
* Windows：10/11

<div id="supported-programming-languages">
  ## 支持的编程语言
</div>

Qoder 支持所有主流语言，并在以下语言上提供增强体验：

* JavaScript、TypeScript、Python、Go、C/C++、C# 和 Java

<div id="data-security">
  ## 数据安全
</div>

<div id="does-qoder-store-my-code">
  ### Qoder 会存储我的代码吗？
</div>

* Qoder 不会存储或分享你的代码。在代码补全过程中会用到你的代码上下文，但这些内容不会被存储，也不会用于其他用途。
* 仅当你明确提交反馈（例如点赞/点踩）时，聊天记录（不包含实际代码）才可能被匿名化，用于算法改进。

详情参见 [隐私政策](https://qoder.com/privacy-policy)。

<div id="is-my-code-snippet-shared-with-other-users">
  ### 我的代码片段会与其他用户共享吗？
</div>

不会。系统不会将你的代码片段与其他用户共享。在使用大语言模型进行代码补全时，我们需要获取你的代码信息来完成补全，但这些上下文信息不会被存储，也不会用于任何其他用途。

<div id="can-i-directly-use-the-code-generated-by-qoder">
  ### 我可以直接使用 Qoder 生成的代码吗？
</div>

Qoder 生成的代码仅作参考，无法保证其可用性。开发者应自行审查并决定是否采用。

<div id="troubleshooting-common-issues">
  ## 疑难排查与常见问题
</div>

<div id="what-should-i-do-if-i-get-a-system-error-in-quest-mode-and-the-repo-wiki">
  ### 如果我在 Quest Mode 和 Repo Wiki 中遇到“System Error”，该怎么办？
</div>

请更新至 Qoder v0.2.1 或更高版本。旧版本不支持这些功能。

<div id="high-cpu-or-memory-usage">
  ### CPU 或内存占用过高
</div>

* 大型项目在进行代码索引时可能会占用大量资源。
* 将不需要索引的文件模式或目录添加到项目根目录的 `.qoderignore`（类似于 `.gitignore`）。
* 编辑 `.qoderignore` 后，请重启 Qoder。

<div id="qoder-extension-host-crash">
  ### Qoder 扩展宿主崩溃
</div>

**错误**：“extension host terminated unexpectedly 3 times within the last 5 minutes”

* 可能由内存泄漏引起。
* 使用 [extension bisect](https://code.visualstudio.com/blogs/2021/02/16/extension-bisect) 确认是否由 Qoder 导致问题。
* 尝试重新安装 Qoder 并重启。
* 在 Windows 上，确保安全软件未拦截或阻止 Qoder。

如果问题仍然存在，请发送邮件至 [contact@qoder.com](mailto:contact@qoder.com)。

* 操作系统及 Qoder 版本
* 复现步骤
* Qoder 详细日志（运行 `qoder --verbose`）
* 如需崩溃转储：运行 `qoder --crash-reporter-directory <directory>`，复现错误，并将生成的 `.dmp` 文件发送给我们。

<div id="support">
  ## 支持
</div>

如需更多帮助，请通过 [contact@qoder.com](mailto:contact@qoder.com) 与我们联系。

---

@weixin.jpg

![获取更多Qoder、Trae 团队版优惠](../../../../weixin.jpg)
