---
title: WPF 安全性策略 – 安全性工程
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: a042f0ae1c7673f7d21b39580db3d373835939cd
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353827"
---
# <a name="wpf-security-strategy---security-engineering"></a><span data-ttu-id="6d3d9-102">WPF 安全性策略 – 安全性工程</span><span class="sxs-lookup"><span data-stu-id="6d3d9-102">WPF Security Strategy - Security Engineering</span></span>
<span data-ttu-id="6d3d9-103">高可信度電腦運算是一項 Microsoft 開發案，用於確保生產安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-103">Trustworthy Computing is a Microsoft initiative for ensuring the production of secure code.</span></span> <span data-ttu-id="6d3d9-104">「可信賴的運算」計畫的關鍵要素是 Microsoft 安全性開發週期 (SDL) （SDL）。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-104">A key element of the Trustworthy Computing initiative is the Microsoft Security Development Lifecycle (SDL).</span></span> <span data-ttu-id="6d3d9-105">SDL 是一種工程實務，與標準工程程式搭配使用，以促進安全程式碼的傳遞。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-105">The SDL is an engineering practice that is used in conjunction with standard engineering processes to facilitate the delivery of secure code.</span></span> <span data-ttu-id="6d3d9-106">SDL 包含十個階段，結合了最佳作法與正規化、measurability 和其他結構，包括：</span><span class="sxs-lookup"><span data-stu-id="6d3d9-106">The SDL consists of ten phases that combine best practices with formalization, measurability, and additional structure, including:</span></span>  
  
- <span data-ttu-id="6d3d9-107">安全性設計分析</span><span class="sxs-lookup"><span data-stu-id="6d3d9-107">Security design analysis</span></span>  
  
- <span data-ttu-id="6d3d9-108">以工具為基礎的品質檢查</span><span class="sxs-lookup"><span data-stu-id="6d3d9-108">Tool-based quality checks</span></span>  
  
- <span data-ttu-id="6d3d9-109">滲透測試</span><span class="sxs-lookup"><span data-stu-id="6d3d9-109">Penetration testing</span></span>  
  
- <span data-ttu-id="6d3d9-110">最終安全性檢閱</span><span class="sxs-lookup"><span data-stu-id="6d3d9-110">Final security review</span></span>  
  
- <span data-ttu-id="6d3d9-111">產品發行後安全性管理</span><span class="sxs-lookup"><span data-stu-id="6d3d9-111">Post release product security management</span></span>  
  
## <a name="wpf-specifics"></a><span data-ttu-id="6d3d9-112">WPF 特性</span><span class="sxs-lookup"><span data-stu-id="6d3d9-112">WPF Specifics</span></span>  
 <span data-ttu-id="6d3d9-113">@No__t 0 工程小組會同時套用和擴充 SDL，其結合包括下列重要層面：</span><span class="sxs-lookup"><span data-stu-id="6d3d9-113">The [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] engineering team both applies and extends the SDL, the combination of which includes the following key aspects:</span></span>  
  
 [<span data-ttu-id="6d3d9-114">威脅模型</span><span class="sxs-lookup"><span data-stu-id="6d3d9-114">Threat Modeling</span></span>](#threat_modeling)  
  
 [<span data-ttu-id="6d3d9-115">安全性分析和編輯工具</span><span class="sxs-lookup"><span data-stu-id="6d3d9-115">Security Analysis and Editing Tools</span></span>](#tools)  
  
 [<span data-ttu-id="6d3d9-116">測試技術</span><span class="sxs-lookup"><span data-stu-id="6d3d9-116">Testing Techniques</span></span>](#techniques)  
  
 [<span data-ttu-id="6d3d9-117">重要程式碼管理</span><span class="sxs-lookup"><span data-stu-id="6d3d9-117">Critical Code Management</span></span>](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a><span data-ttu-id="6d3d9-118">威脅模型</span><span class="sxs-lookup"><span data-stu-id="6d3d9-118">Threat Modeling</span></span>  
 <span data-ttu-id="6d3d9-119">威脅模型化是 SDL 的核心元件，用來分析系統以判斷潛在的安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-119">Threat modeling is a core component of the SDL, and is used to profile a system to determine potential security vulnerabilities.</span></span> <span data-ttu-id="6d3d9-120">一旦識別出漏洞，威脅模型也可確保適當的安全防護已就位。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-120">Once the vulnerabilities are identified, threat modeling also ensures that appropriate mitigations are in place.</span></span>  
  
 <span data-ttu-id="6d3d9-121">高階的威脅模型牽涉到下列重要步驟，藉由使用雜貨店做為範例：</span><span class="sxs-lookup"><span data-stu-id="6d3d9-121">At a high level, threat modeling involves the following key steps by using a grocery store as an example:</span></span>  
  
1. <span data-ttu-id="6d3d9-122">**識別資產**。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-122">**Identifying Assets**.</span></span> <span data-ttu-id="6d3d9-123">雜貨店的資產可能包含員工、保險箱、收銀機和庫存。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-123">A grocery store's assets might include employees, a safe, cash registers, and inventory.</span></span>  
  
2. <span data-ttu-id="6d3d9-124">**列舉進入點**。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-124">**Enumerating Entry Points**.</span></span> <span data-ttu-id="6d3d9-125">雜貨店的進入點可能包含前門和後門、窗戶、卸貨平台和空調設備。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-125">A grocery store's entry points might include the front and back doors, windows, the loading dock, and air conditioning units.</span></span>  
  
3. <span data-ttu-id="6d3d9-126">**使用進入點調查針對資產的攻擊**。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-126">**Investigating Attacks against Assets using Entry Points**.</span></span> <span data-ttu-id="6d3d9-127">一次可能的攻擊或許會經由「空調」進入點，以雜貨店的「保險箱」資產為攻擊目標；空調設備可能被拆下，讓保險箱能從中被拖出來，搬到商店外。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-127">One possible attack could target a grocery store's *safe* asset through the *air conditioning* entry point; the air conditioning unit could be unscrewed to allow the safe to be pulled up through it and out of the store.</span></span>  
  
 <span data-ttu-id="6d3d9-128">威脅模型套用到整個 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 並包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="6d3d9-128">Threat modeling is applied throughout [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] and includes the following:</span></span>  
  
- <span data-ttu-id="6d3d9-129">[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 剖析器會如何讀取檔案，將文字對應到對應的物件模型類別，並建立實際的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-129">How the [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] parser reads files, maps text to corresponding object model classes, and creates the actual code.</span></span>  
  
- <span data-ttu-id="6d3d9-130">如何建立視窗控制代碼 (hWnd)、傳送訊息，以及用來呈現視窗的內容。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-130">How a window handle (hWnd) is created, sends messages, and is used for rendering the contents of a window.</span></span>  
  
- <span data-ttu-id="6d3d9-131">資料繫結如何取得資源，並與系統互動。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-131">How data binding obtains resources and interacts with the system.</span></span>  
  
 <span data-ttu-id="6d3d9-132">在開發過程中，這些威脅模型對於識別安全性設計需求和威脅的安全防護相當重要。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-132">These threat models are important for identifying security design requirements and threat mitigations during the development process.</span></span>  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a><span data-ttu-id="6d3d9-133">來源分析和編輯工具</span><span class="sxs-lookup"><span data-stu-id="6d3d9-133">Source Analysis and Editing Tools</span></span>  
 <span data-ttu-id="6d3d9-134">除了 SDL 的手動安全性程式碼審查元素之外，@no__t 0 團隊也使用數種工具進行來源分析，並將相關的編輯專案用於減少安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-134">In addition to the manual security code review elements of the SDL, the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] team uses several tools for source analysis and associated edits to decrease security vulnerabilities.</span></span> <span data-ttu-id="6d3d9-135">使用廣泛的來源工具，包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="6d3d9-135">A wide range of source tools are used, and include the following:</span></span>  
  
- <span data-ttu-id="6d3d9-136">**FXCop**：尋找 managed 程式碼中的常見安全性問題，範圍從繼承規則到代碼啟用安全性使用方式，到如何安全地與非受控程式碼交互操作。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-136">**FXCop**: Finds common security issues in managed code ranging from inheritance rules to code access security usage to how to safely interoperate with unmanaged code.</span></span> <span data-ttu-id="6d3d9-137">請參閱 [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29)。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-137">See [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).</span></span>  
  
- <span data-ttu-id="6d3d9-138">**Prefix/Prefast**：尋找非受控程式碼中的安全性弱點和常見的安全性問題，例如緩衝區溢位、格式字串問題和錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-138">**Prefix/Prefast**: Finds security vulnerabilities and common security issues in unmanaged code such as buffer overruns, format string issues, and error checking.</span></span>  
  
- <span data-ttu-id="6d3d9-139">**禁止的 api**：搜尋原始程式碼，以識別已知會造成安全性問題的函式意外使用，例如 `strcpy`。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-139">**Banned APIs**: Searches source code to identify accidental usage of functions that are well-known for causing security issues, such as `strcpy`.</span></span> <span data-ttu-id="6d3d9-140">一旦識別出來，這些函式會取代為更安全的替代專案。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-140">Once identified, these functions are replaced with alternatives that are more secure.</span></span>  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a><span data-ttu-id="6d3d9-141">測試技術</span><span class="sxs-lookup"><span data-stu-id="6d3d9-141">Testing Techniques</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="6d3d9-142">使用不同的安全性測試技術，包含：</span><span class="sxs-lookup"><span data-stu-id="6d3d9-142">uses a variety of security testing techniques that include:</span></span>  
  
- <span data-ttu-id="6d3d9-143">**白箱測試**：測試人員會查看原始程式碼，然後建立惡意探勘測試。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-143">**Whitebox Testing**: Testers view source code, and then build exploit tests.</span></span>
  
- <span data-ttu-id="6d3d9-144">**黑箱測試**：測試人員會藉由檢查 API 和功能來嘗試找出安全性攻擊，然後嘗試攻擊產品。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-144">**Blackbox Testing**: Testers try to find security exploits by examining the API and features, and then try to attack the product.</span></span>  
  
- <span data-ttu-id="6d3d9-145">**回歸其他產品的安全性問題**：在相關的情況下，會測試來自相關產品的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-145">**Regressing Security Issues from other Products**: Where relevant, security issues from related products are tested.</span></span> <span data-ttu-id="6d3d9-146">例如，已識別 Internet Explorer 大約60安全性問題的適當變種，並嘗試其對 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 的適用性。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-146">For example, appropriate variants of approximately sixty security issues for Internet Explorer have been identified and tried for their applicability to [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
- <span data-ttu-id="6d3d9-147">以**工具為基礎的滲透測試透過檔案模糊**處理：檔案模糊處理是透過各種輸入來利用檔案讀取器的輸入範圍。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-147">**Tools-Based Penetration Testing through File Fuzzing**: File fuzzing is the exploitation of a file reader's input range through a variety of inputs.</span></span> <span data-ttu-id="6d3d9-148">[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 中使用這項技術的其中一個範例是用來檢查影像解碼程式碼中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-148">One example in [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] where this technique is used is to check for failure in image decoding code.</span></span>  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a><span data-ttu-id="6d3d9-149">重要程式碼管理</span><span class="sxs-lookup"><span data-stu-id="6d3d9-149">Critical Code Management</span></span>  
 <span data-ttu-id="6d3d9-150">對於 [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]，[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 會使用 .NET Framework 支援來建立安全性沙箱，以標示和追蹤提升許可權的安全性關鍵程式碼（請參閱[WPF 安全性策略-平臺安全性](wpf-security-strategy-platform-security.md)中的**安全性關鍵方法**）。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-150">For [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] builds a security sandbox by using .NET Framework support for marking and tracking security-critical code that elevates privileges (see **Security-Critical Methodology** in [WPF Security Strategy - Platform Security](wpf-security-strategy-platform-security.md)).</span></span> <span data-ttu-id="6d3d9-151">假設在安全性關鍵程式碼上的安全性需求很高，這類程式碼會接收額外層級的來源管理控制和安全性稽核。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-151">Given the high security quality requirements on security critical code, such code receives an additional level of source management control and security audit.</span></span> <span data-ttu-id="6d3d9-152">大約 5% 到 10%的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 由經過專門的檢閱小組檢閱的安全性關鍵程式碼所組成。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-152">Approximately 5% to 10% of [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] consists of security-critical code, which is reviewed by a dedicated reviewing team.</span></span> <span data-ttu-id="6d3d9-153">原始程式碼和簽入程序是由追蹤安全性關鍵程式碼來管理，以及對應每個重要的實體 (也就是一個包含關鍵程式碼的方法) 至其登出狀態。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-153">The source code and check-in process is managed by tracking security critical code and mapping each critical entity (i.e. a method that contains critical code) to its sign off state.</span></span> <span data-ttu-id="6d3d9-154">登出狀態包含一或多個檢閱者的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-154">The sign off state includes the names of one or more reviewers.</span></span> <span data-ttu-id="6d3d9-155">每個 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 的每日建置會比較該關鍵程式碼和前一個建置的關鍵程式碼，以檢查未經核准的變更。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-155">Each daily build of [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] compares the critical code to that in previous builds to check for unapproved changes.</span></span> <span data-ttu-id="6d3d9-156">如果工程師修改未經檢閱小組核准的關鍵程式碼，它會被識別並被立即修正。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-156">If an engineer modifies critical code without approval from the reviewing team, it is identified and fixed immediately.</span></span> <span data-ttu-id="6d3d9-157">此程序能在 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 沙箱程式碼上套用和維護特別高層級的監督。</span><span class="sxs-lookup"><span data-stu-id="6d3d9-157">This process enables the application and maintenance of an especially high level of scrutiny over [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sandbox code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3d9-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d3d9-158">See also</span></span>

- [<span data-ttu-id="6d3d9-159">安全性</span><span class="sxs-lookup"><span data-stu-id="6d3d9-159">Security</span></span>](security-wpf.md)
- [<span data-ttu-id="6d3d9-160">WPF 部分信任安全性</span><span class="sxs-lookup"><span data-stu-id="6d3d9-160">WPF Partial Trust Security</span></span>](wpf-partial-trust-security.md)
- [<span data-ttu-id="6d3d9-161">WPF 安全性策略 – 平台安全性</span><span class="sxs-lookup"><span data-stu-id="6d3d9-161">WPF Security Strategy - Platform Security</span></span>](wpf-security-strategy-platform-security.md)
- [<span data-ttu-id="6d3d9-162">高可信度電腦運算</span><span class="sxs-lookup"><span data-stu-id="6d3d9-162">Trustworthy Computing</span></span>](https://www.microsoft.com/mscorp/twc/default.mspx)
- [<span data-ttu-id="6d3d9-163">.NET 中的安全性</span><span class="sxs-lookup"><span data-stu-id="6d3d9-163">Security in .NET</span></span>](../../standard/security/index.md)
