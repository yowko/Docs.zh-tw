---
title: 安全戰略和工程
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
ms.openlocfilehash: 970627c5de4964ebd5331c488152022fda55bd74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174559"
---
# <a name="wpf-security-strategy---security-engineering"></a><span data-ttu-id="d0393-102">WPF 安全性策略 – 安全性工程</span><span class="sxs-lookup"><span data-stu-id="d0393-102">WPF Security Strategy - Security Engineering</span></span>
<span data-ttu-id="d0393-103">高可信度電腦運算是一項 Microsoft 開發案，用於確保生產安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d0393-103">Trustworthy Computing is a Microsoft initiative for ensuring the production of secure code.</span></span> <span data-ttu-id="d0393-104">可信計算計畫的一個關鍵要素是 Microsoft 安全開發生命週期 （SDL）。</span><span class="sxs-lookup"><span data-stu-id="d0393-104">A key element of the Trustworthy Computing initiative is the Microsoft Security Development Lifecycle (SDL).</span></span> <span data-ttu-id="d0393-105">SDL 是一種工程實踐，它與標準工程流程結合使用，以方便安全代碼的交付。</span><span class="sxs-lookup"><span data-stu-id="d0393-105">The SDL is an engineering practice that is used in conjunction with standard engineering processes to facilitate the delivery of secure code.</span></span> <span data-ttu-id="d0393-106">SDL 由十個階段組成，將最佳實踐與形式化、可測量性和其他結構相結合，包括：</span><span class="sxs-lookup"><span data-stu-id="d0393-106">The SDL consists of ten phases that combine best practices with formalization, measurability, and additional structure, including:</span></span>  
  
- <span data-ttu-id="d0393-107">安全性設計分析</span><span class="sxs-lookup"><span data-stu-id="d0393-107">Security design analysis</span></span>  
  
- <span data-ttu-id="d0393-108">以工具為基礎的品質檢查</span><span class="sxs-lookup"><span data-stu-id="d0393-108">Tool-based quality checks</span></span>  
  
- <span data-ttu-id="d0393-109">滲透測試</span><span class="sxs-lookup"><span data-stu-id="d0393-109">Penetration testing</span></span>  
  
- <span data-ttu-id="d0393-110">最終安全性檢閱</span><span class="sxs-lookup"><span data-stu-id="d0393-110">Final security review</span></span>  
  
- <span data-ttu-id="d0393-111">產品發行後安全性管理</span><span class="sxs-lookup"><span data-stu-id="d0393-111">Post release product security management</span></span>  
  
## <a name="wpf-specifics"></a><span data-ttu-id="d0393-112">WPF 特性</span><span class="sxs-lookup"><span data-stu-id="d0393-112">WPF Specifics</span></span>  
 <span data-ttu-id="d0393-113">[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]工程團隊同時應用和擴展 SDL，其組合包括以下關鍵方面：</span><span class="sxs-lookup"><span data-stu-id="d0393-113">The [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] engineering team both applies and extends the SDL, the combination of which includes the following key aspects:</span></span>  
  
 [<span data-ttu-id="d0393-114">威脅建模</span><span class="sxs-lookup"><span data-stu-id="d0393-114">Threat Modeling</span></span>](#threat_modeling)  
  
 [<span data-ttu-id="d0393-115">安全性分析和編輯工具</span><span class="sxs-lookup"><span data-stu-id="d0393-115">Security Analysis and Editing Tools</span></span>](#tools)  
  
 [<span data-ttu-id="d0393-116">測試技術</span><span class="sxs-lookup"><span data-stu-id="d0393-116">Testing Techniques</span></span>](#techniques)  
  
 [<span data-ttu-id="d0393-117">重要程式碼管理</span><span class="sxs-lookup"><span data-stu-id="d0393-117">Critical Code Management</span></span>](#critical_code)  
  
<a name="threat_modeling"></a>
### <a name="threat-modeling"></a><span data-ttu-id="d0393-118">威脅模型</span><span class="sxs-lookup"><span data-stu-id="d0393-118">Threat Modeling</span></span>  
 <span data-ttu-id="d0393-119">威脅建模是 SDL 的核心元件，用於分析系統以確定潛在的安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="d0393-119">Threat modeling is a core component of the SDL, and is used to profile a system to determine potential security vulnerabilities.</span></span> <span data-ttu-id="d0393-120">一旦識別出漏洞，威脅模型也可確保適當的安全防護已就位。</span><span class="sxs-lookup"><span data-stu-id="d0393-120">Once the vulnerabilities are identified, threat modeling also ensures that appropriate mitigations are in place.</span></span>  
  
 <span data-ttu-id="d0393-121">高階的威脅模型牽涉到下列重要步驟，藉由使用雜貨店做為範例：</span><span class="sxs-lookup"><span data-stu-id="d0393-121">At a high level, threat modeling involves the following key steps by using a grocery store as an example:</span></span>  
  
1. <span data-ttu-id="d0393-122">**識別資產**。</span><span class="sxs-lookup"><span data-stu-id="d0393-122">**Identifying Assets**.</span></span> <span data-ttu-id="d0393-123">雜貨店的資產可能包含員工、保險箱、收銀機和庫存。</span><span class="sxs-lookup"><span data-stu-id="d0393-123">A grocery store's assets might include employees, a safe, cash registers, and inventory.</span></span>  
  
2. <span data-ttu-id="d0393-124">**列舉進入點**。</span><span class="sxs-lookup"><span data-stu-id="d0393-124">**Enumerating Entry Points**.</span></span> <span data-ttu-id="d0393-125">雜貨店的進入點可能包含前門和後門、窗戶、卸貨平台和空調設備。</span><span class="sxs-lookup"><span data-stu-id="d0393-125">A grocery store's entry points might include the front and back doors, windows, the loading dock, and air conditioning units.</span></span>  
  
3. <span data-ttu-id="d0393-126">**使用進入點調查針對資產的攻擊**。</span><span class="sxs-lookup"><span data-stu-id="d0393-126">**Investigating Attacks against Assets using Entry Points**.</span></span> <span data-ttu-id="d0393-127">一次可能的攻擊或許會經由「空調」\*\* 進入點，以雜貨店的「保險箱」\*\* 資產為攻擊目標；空調設備可能被拆下，讓保險箱能從中被拖出來，搬到商店外。</span><span class="sxs-lookup"><span data-stu-id="d0393-127">One possible attack could target a grocery store's *safe* asset through the *air conditioning* entry point; the air conditioning unit could be unscrewed to allow the safe to be pulled up through it and out of the store.</span></span>  
  
 <span data-ttu-id="d0393-128">威脅模型套用到整個 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 並包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="d0393-128">Threat modeling is applied throughout [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] and includes the following:</span></span>  
  
- <span data-ttu-id="d0393-129">[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 剖析器會如何讀取檔案，將文字對應到對應的物件模型類別，並建立實際的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d0393-129">How the [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] parser reads files, maps text to corresponding object model classes, and creates the actual code.</span></span>  
  
- <span data-ttu-id="d0393-130">如何建立視窗控制代碼 (hWnd)、傳送訊息，以及用來呈現視窗的內容。</span><span class="sxs-lookup"><span data-stu-id="d0393-130">How a window handle (hWnd) is created, sends messages, and is used for rendering the contents of a window.</span></span>  
  
- <span data-ttu-id="d0393-131">資料繫結如何取得資源，並與系統互動。</span><span class="sxs-lookup"><span data-stu-id="d0393-131">How data binding obtains resources and interacts with the system.</span></span>  
  
 <span data-ttu-id="d0393-132">在開發過程中，這些威脅模型對於識別安全性設計需求和威脅的安全防護相當重要。</span><span class="sxs-lookup"><span data-stu-id="d0393-132">These threat models are important for identifying security design requirements and threat mitigations during the development process.</span></span>  
  
<a name="tools"></a>
### <a name="source-analysis-and-editing-tools"></a><span data-ttu-id="d0393-133">來源分析和編輯工具</span><span class="sxs-lookup"><span data-stu-id="d0393-133">Source Analysis and Editing Tools</span></span>  
 <span data-ttu-id="d0393-134">除了 SDL 的手動安全代碼審查元素外，[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]團隊還使用多種工具進行源分析和相關的編輯，以減少安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="d0393-134">In addition to the manual security code review elements of the SDL, the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] team uses several tools for source analysis and associated edits to decrease security vulnerabilities.</span></span> <span data-ttu-id="d0393-135">使用廣泛的來源工具，包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="d0393-135">A wide range of source tools are used, and include the following:</span></span>  
  
- <span data-ttu-id="d0393-136">**FXCop**：尋找在 Managed 程式碼中的常見安全性問題，從程式碼存取安全性之使用狀況的繼承規則，到如何安全地相互操作 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d0393-136">**FXCop**: Finds common security issues in managed code ranging from inheritance rules to code access security usage to how to safely interoperate with unmanaged code.</span></span> <span data-ttu-id="d0393-137">請參閱 [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29)。</span><span class="sxs-lookup"><span data-stu-id="d0393-137">See [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).</span></span>  
  
- <span data-ttu-id="d0393-138">**Prefix/Prefast**：找出 Unmanaged 程式碼中的安全性漏洞及常見安全性問題，例如緩衝區滿溢、格式字串問題和錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="d0393-138">**Prefix/Prefast**: Finds security vulnerabilities and common security issues in unmanaged code such as buffer overruns, format string issues, and error checking.</span></span>  
  
- <span data-ttu-id="d0393-139">**禁止的應用程式開發介面**：搜尋原始程式碼，來識別已知會造成安全性問題之函式的意外使用，例如 `strcpy`。</span><span class="sxs-lookup"><span data-stu-id="d0393-139">**Banned APIs**: Searches source code to identify accidental usage of functions that are well-known for causing security issues, such as `strcpy`.</span></span> <span data-ttu-id="d0393-140">一旦確定，這些函數將被更安全的替代項替換。</span><span class="sxs-lookup"><span data-stu-id="d0393-140">Once identified, these functions are replaced with alternatives that are more secure.</span></span>  
  
<a name="techniques"></a>
### <a name="testing-techniques"></a><span data-ttu-id="d0393-141">測試技術</span><span class="sxs-lookup"><span data-stu-id="d0393-141">Testing Techniques</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="d0393-142">使用不同的安全性測試技術，包含：</span><span class="sxs-lookup"><span data-stu-id="d0393-142">uses a variety of security testing techniques that include:</span></span>  
  
- <span data-ttu-id="d0393-143">**白盒測試**：測試人員查看原始程式碼，然後構建漏洞利用測試。</span><span class="sxs-lookup"><span data-stu-id="d0393-143">**Whitebox Testing**: Testers view source code, and then build exploit tests.</span></span>
  
- <span data-ttu-id="d0393-144">**黑箱測試**：測試人員藉由檢查應用程式開發介面和功能，試著找出安全性漏洞，然後嘗試攻擊產品。</span><span class="sxs-lookup"><span data-stu-id="d0393-144">**Blackbox Testing**: Testers try to find security exploits by examining the API and features, and then try to attack the product.</span></span>  
  
- <span data-ttu-id="d0393-145">**從其他產品減輕安全性問題**：如果相關，則測試來自相關產品的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="d0393-145">**Regressing Security Issues from other Products**: Where relevant, security issues from related products are tested.</span></span> <span data-ttu-id="d0393-146">例如，已確定並嘗試 Internet Explorer 大約 60 個安全問題的適當變體，並嘗試它們[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]適用于 。</span><span class="sxs-lookup"><span data-stu-id="d0393-146">For example, appropriate variants of approximately sixty security issues for Internet Explorer have been identified and tried for their applicability to [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
- <span data-ttu-id="d0393-147">**透過檔案模糊測試進行以工具為基礎的滲透測試**：檔案模糊測試是透過各種輸入來惡意探索檔案讀取器的輸入範圍。</span><span class="sxs-lookup"><span data-stu-id="d0393-147">**Tools-Based Penetration Testing through File Fuzzing**: File fuzzing is the exploitation of a file reader's input range through a variety of inputs.</span></span> <span data-ttu-id="d0393-148">[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 中使用這項技術的其中一個範例是用來檢查影像解碼程式碼中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d0393-148">One example in [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] where this technique is used is to check for failure in image decoding code.</span></span>  
  
<a name="critical_code"></a>
### <a name="critical-code-management"></a><span data-ttu-id="d0393-149">重要程式碼管理</span><span class="sxs-lookup"><span data-stu-id="d0393-149">Critical Code Management</span></span>  
 <span data-ttu-id="d0393-150">對於 XAML 瀏覽器應用程式 （XBAPs），[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]使用 .NET Framework 支援來標記和跟蹤提升特權的安全關鍵代碼來構建安全沙箱（請參閱[WPF 安全性原則](wpf-security-strategy-platform-security.md)**中的安全關鍵方法**- 平臺安全）。</span><span class="sxs-lookup"><span data-stu-id="d0393-150">For XAML browser applications (XBAPs), [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] builds a security sandbox by using .NET Framework support for marking and tracking security-critical code that elevates privileges (see **Security-Critical Methodology** in [WPF Security Strategy - Platform Security](wpf-security-strategy-platform-security.md)).</span></span> <span data-ttu-id="d0393-151">假設在安全性關鍵程式碼上的安全性需求很高，這類程式碼會接收額外層級的來源管理控制和安全性稽核。</span><span class="sxs-lookup"><span data-stu-id="d0393-151">Given the high security quality requirements on security critical code, such code receives an additional level of source management control and security audit.</span></span> <span data-ttu-id="d0393-152">大約 5% 到 10%的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 由經過專門的檢閱小組檢閱的安全性關鍵程式碼所組成。</span><span class="sxs-lookup"><span data-stu-id="d0393-152">Approximately 5% to 10% of [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] consists of security-critical code, which is reviewed by a dedicated reviewing team.</span></span> <span data-ttu-id="d0393-153">原始程式碼和簽入程序是由追蹤安全性關鍵程式碼來管理，以及對應每個重要的實體 (也就是一個包含關鍵程式碼的方法) 至其登出狀態。</span><span class="sxs-lookup"><span data-stu-id="d0393-153">The source code and check-in process is managed by tracking security critical code and mapping each critical entity (i.e. a method that contains critical code) to its sign off state.</span></span> <span data-ttu-id="d0393-154">登出狀態包含一或多個檢閱者的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0393-154">The sign off state includes the names of one or more reviewers.</span></span> <span data-ttu-id="d0393-155">每個 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 的每日建置會比較該關鍵程式碼和前一個建置的關鍵程式碼，以檢查未經核准的變更。</span><span class="sxs-lookup"><span data-stu-id="d0393-155">Each daily build of [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] compares the critical code to that in previous builds to check for unapproved changes.</span></span> <span data-ttu-id="d0393-156">如果工程師修改未經檢閱小組核准的關鍵程式碼，它會被識別並被立即修正。</span><span class="sxs-lookup"><span data-stu-id="d0393-156">If an engineer modifies critical code without approval from the reviewing team, it is identified and fixed immediately.</span></span> <span data-ttu-id="d0393-157">此程序能在 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 沙箱程式碼上套用和維護特別高層級的監督。</span><span class="sxs-lookup"><span data-stu-id="d0393-157">This process enables the application and maintenance of an especially high level of scrutiny over [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sandbox code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0393-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0393-158">See also</span></span>

- [<span data-ttu-id="d0393-159">安全性</span><span class="sxs-lookup"><span data-stu-id="d0393-159">Security</span></span>](security-wpf.md)
- [<span data-ttu-id="d0393-160">WPF 部分信任安全性</span><span class="sxs-lookup"><span data-stu-id="d0393-160">WPF Partial Trust Security</span></span>](wpf-partial-trust-security.md)
- [<span data-ttu-id="d0393-161">WPF 安全性策略 – 平台安全性</span><span class="sxs-lookup"><span data-stu-id="d0393-161">WPF Security Strategy - Platform Security</span></span>](wpf-security-strategy-platform-security.md)
- [<span data-ttu-id="d0393-162">可信任的電腦運算</span><span class="sxs-lookup"><span data-stu-id="d0393-162">Trustworthy Computing</span></span>](https://www.microsoft.com/mscorp/twc/default.mspx)
- [<span data-ttu-id="d0393-163">.NET 的安全性</span><span class="sxs-lookup"><span data-stu-id="d0393-163">Security in .NET</span></span>](../../standard/security/index.md)
