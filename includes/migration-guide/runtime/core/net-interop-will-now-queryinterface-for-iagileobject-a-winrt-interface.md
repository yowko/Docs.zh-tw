---
ms.openlocfilehash: 65fa5d8629ce8e426cf1623590a056e5cad0b91f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496719"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a><span data-ttu-id="08917-101">.NET Interop 現會進行 IAgileObject 的 QueryInterface 作業 (WinRT 介面)</span><span class="sxs-lookup"><span data-stu-id="08917-101">.NET Interop will now QueryInterface for IAgileObject (a WinRT interface)</span></span>

#### <a name="details"></a><span data-ttu-id="08917-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="08917-102">Details</span></span>

<span data-ttu-id="08917-103">從 .NET Framework 4.8 開始，當您搭配使用 WinRT 事件與 .NET 委派時，Windows 會進行 IAgileObject 的 QI 作業。</span><span class="sxs-lookup"><span data-stu-id="08917-103">When using a WinRT event with a .NET delegate, Windows will QI for IAgileObject starting with the .NET Framework 4.8.</span></span>  <span data-ttu-id="08917-104">在舊版 .NET Framework 中，執行階段會讓該 QI 失敗，而無法訂閱此事件。</span><span class="sxs-lookup"><span data-stu-id="08917-104">In previous versions of the .NET Framework, the runtime would fail that QI, and the event could not be subscribed.</span></span><ul><li><span data-ttu-id="08917-105">[ x ] Quirked</span><span class="sxs-lookup"><span data-stu-id="08917-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="08917-106">建議</span><span class="sxs-lookup"><span data-stu-id="08917-106">Suggestion</span></span>

<span data-ttu-id="08917-107">如果啟用 IAgileObject 的 QI 作業會導致執行中斷，您可以進行下列設定來停用此程式碼。</span><span class="sxs-lookup"><span data-stu-id="08917-107">If enabling the QI for IAgileObject breaks execution, you can disable this code by setting the following configuration.</span></span> <h4><span data-ttu-id="08917-108">方法1：環境變數</span><span class="sxs-lookup"><span data-stu-id="08917-108">Method 1: Environment variable</span></span></h4> <span data-ttu-id="08917-109">設定下列環境變數：COMPLUS_DisableCCWSupportIAgileObject=1 這個方法會影響任何繼承此環境變數的環境。</span><span class="sxs-lookup"><span data-stu-id="08917-109">Set the following environment variable:COMPLUS_DisableCCWSupportIAgileObject=1This method affects any environment that inherits this environment variable.</span></span> <span data-ttu-id="08917-110">這可能只是單一主控台會話，如果您在全域設定環境變數，它可能會影響整部電腦。</span><span class="sxs-lookup"><span data-stu-id="08917-110">This might be just a single console session, or it might affect the entire machine if you set the environment variable globally.</span></span> <span data-ttu-id="08917-111">環境變數名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="08917-111">The environment variable name is not case-sensitive.</span></span> <h4><span data-ttu-id="08917-112">方法2：登錄</span><span class="sxs-lookup"><span data-stu-id="08917-112">Method 2: Registry</span></span></h4> <span data-ttu-id="08917-113">使用登錄編輯程式 ( # A0) 中，找出下列其中一個子機碼： HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER \SOFTWARE\Microsoft.NETFrameworkThen 新增下列子機碼：值名稱： DisableCCWSupportIAgileObject 類型： DWORD (32 位) 值 (也稱為 REG_WORD) 值：1您可以使用 Windows REG.EXE 工具，從命令列或腳本環境新增此值。</span><span class="sxs-lookup"><span data-stu-id="08917-113">Using Registry Editor (regedit.exe), find either of the following subkeys:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkThen add the following:Value name: DisableCCWSupportIAgileObject Type: DWORD (32-bit) Value (also called REG_WORD) Value: 1You can use the Windows REG.EXE tool to add this value from a command-line or scripting environment.</span></span> <span data-ttu-id="08917-114">例如：</span><span class="sxs-lookup"><span data-stu-id="08917-114">For example:</span></span><pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre><span data-ttu-id="08917-115">此案例會使用 <code>HKLM</code>，而不是 <code>HKEY_LOCAL_MACHINE</code>。</span><span class="sxs-lookup"><span data-stu-id="08917-115">In this case, <code>HKLM</code> is used instead of <code>HKEY_LOCAL_MACHINE</code>.</span></span> <span data-ttu-id="08917-116">使用 <code>reg add /?</code> 以查看此語法的說明。</span><span class="sxs-lookup"><span data-stu-id="08917-116">Use <code>reg add /?</code> to see help on this syntax.</span></span> <span data-ttu-id="08917-117">登錄值名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="08917-117">The registry value name is not case-sensitive.</span></span>

| <span data-ttu-id="08917-118">名稱</span><span class="sxs-lookup"><span data-stu-id="08917-118">Name</span></span>    | <span data-ttu-id="08917-119">值</span><span class="sxs-lookup"><span data-stu-id="08917-119">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="08917-120">範圍</span><span class="sxs-lookup"><span data-stu-id="08917-120">Scope</span></span>   |<span data-ttu-id="08917-121">Edge</span><span class="sxs-lookup"><span data-stu-id="08917-121">Edge</span></span>|
|<span data-ttu-id="08917-122">版本</span><span class="sxs-lookup"><span data-stu-id="08917-122">Version</span></span>|<span data-ttu-id="08917-123">4.8</span><span class="sxs-lookup"><span data-stu-id="08917-123">4.8</span></span>|
|<span data-ttu-id="08917-124">類型</span><span class="sxs-lookup"><span data-stu-id="08917-124">Type</span></span>|<span data-ttu-id="08917-125">執行階段</span><span class="sxs-lookup"><span data-stu-id="08917-125">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="08917-126">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="08917-126">Affected APIs</span></span>

<span data-ttu-id="08917-127">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="08917-127">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
