---
title: "安全程式碼撰寫方針"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET Framework], security
- code security, options
- security-neutral code
- security [.NET Framework], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3e75f3c74c5966ce5ce22b23f7ba179e903d37aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="secure-coding-guidelines"></a><span data-ttu-id="92fc8-102">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="92fc8-102">Secure Coding Guidelines</span></span>
<span data-ttu-id="92fc8-103">辨識項架構的安全性和程式碼存取安全性提供十分強大的明確機制以實作安全性。</span><span class="sxs-lookup"><span data-stu-id="92fc8-103">Evidence-based security and code access security provide very powerful, explicit mechanisms to implement security.</span></span> <span data-ttu-id="92fc8-104">大部分的應用程式程式碼都只需要使用 .NET Framework 所實作的基礎結構即可。</span><span class="sxs-lookup"><span data-stu-id="92fc8-104">Most application code can simply use the infrastructure implemented by the .NET Framework.</span></span> <span data-ttu-id="92fc8-105">某些情況還需要其他的應用程式特定安全性 (藉由擴充安全性系統或是使用新的臨機操作方法來建置)。</span><span class="sxs-lookup"><span data-stu-id="92fc8-105">In some cases, additional application-specific security is required, built either by extending the security system or by using new ad hoc methods.</span></span>  
  
 <span data-ttu-id="92fc8-106">透過在您的程式碼中使用 .NET Framework 強制使用權限和其他強制方法，您應該可以設置防線，防止惡意程式碼取得您不想讓它取得的資訊，或是執行其他不當動作。</span><span class="sxs-lookup"><span data-stu-id="92fc8-106">Using the .NET Framework-enforced permissions and other enforcement in your code, you should erect barriers to prevent malicious code from obtaining information that you do not want it to have or performing other undesirable actions.</span></span> <span data-ttu-id="92fc8-107">此外，在所有使用受信任程式碼的可預期案例中，您必須在安全性與可用性之間達成平衡。</span><span class="sxs-lookup"><span data-stu-id="92fc8-107">Additionally, you must strike a balance between security and usability in all the expected scenarios using trusted code.</span></span>  
  
 <span data-ttu-id="92fc8-108">本概觀說明設計程式碼以搭配使用安全性系統時，可以採用的不同方式。</span><span class="sxs-lookup"><span data-stu-id="92fc8-108">This overview describes the different ways code can be designed to work with the security system.</span></span>  
  
## <a name="securing-resource-access"></a><span data-ttu-id="92fc8-109">保護資源存取</span><span class="sxs-lookup"><span data-stu-id="92fc8-109">Securing Resource Access</span></span>  
 <span data-ttu-id="92fc8-110">當設計和撰寫程式碼時，您需要保護並限制程式碼對資源的存取，特別是當使用或叫用未知來源的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="92fc8-110">When designing and writing your code, you need to protect and limit the access that code has to resources, especially when using or invoking code of unknown origin.</span></span> <span data-ttu-id="92fc8-111">因此，請牢記下列技術，以確保程式碼是安全的︰</span><span class="sxs-lookup"><span data-stu-id="92fc8-111">So, keep in mind the following techniques to ensure your code is secure:</span></span>  
  
-   <span data-ttu-id="92fc8-112">請勿使用程式碼存取安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="92fc8-112">Do not use Code Access Security (CAS).</span></span>  
  
-   <span data-ttu-id="92fc8-113">請勿使用部分信任程式碼。</span><span class="sxs-lookup"><span data-stu-id="92fc8-113">Do not use partial trusted code.</span></span>  
  
-   <span data-ttu-id="92fc8-114">請勿使用 .NET 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="92fc8-114">Do not use .NET Remoting.</span></span>  
  
-   <span data-ttu-id="92fc8-115">請勿使用分散式元件物件模型 (DCOM)。</span><span class="sxs-lookup"><span data-stu-id="92fc8-115">Do not use Distributed Component Object Model (DCOM).</span></span>  
  
-   <span data-ttu-id="92fc8-116">請勿使用二進位格式器。</span><span class="sxs-lookup"><span data-stu-id="92fc8-116">Do not use binary formatters.</span></span>  
  
 <span data-ttu-id="92fc8-117">程式碼存取安全性與安全性透明的程式碼，將不會如同部分程式碼受信任的安全性界限般受到支援。</span><span class="sxs-lookup"><span data-stu-id="92fc8-117">Code Access Security and Security-Transparent Code will not be supported as a security boundary with partially trusted code.</span></span> <span data-ttu-id="92fc8-118">建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。</span><span class="sxs-lookup"><span data-stu-id="92fc8-118">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="92fc8-119">替代的安全性措施包括︰</span><span class="sxs-lookup"><span data-stu-id="92fc8-119">The alternative security measures are:</span></span>  
  
-   <span data-ttu-id="92fc8-120">虛擬化</span><span class="sxs-lookup"><span data-stu-id="92fc8-120">Virtualization</span></span>  
  
-   <span data-ttu-id="92fc8-121">AppContainers</span><span class="sxs-lookup"><span data-stu-id="92fc8-121">AppContainers</span></span>  
  
-   <span data-ttu-id="92fc8-122">作業系統 (OS) 使用者和權限</span><span class="sxs-lookup"><span data-stu-id="92fc8-122">Operating system (OS) users and permissions</span></span>  
  
-   <span data-ttu-id="92fc8-123">Hyper-V 容器</span><span class="sxs-lookup"><span data-stu-id="92fc8-123">Hyper-V containers</span></span>  
  
## <a name="security-neutral-code"></a><span data-ttu-id="92fc8-124">安全性中性的程式碼</span><span class="sxs-lookup"><span data-stu-id="92fc8-124">Security-Neutral Code</span></span>  
 <span data-ttu-id="92fc8-125">安全性中性的程式碼與安全性系統並無明顯關聯。</span><span class="sxs-lookup"><span data-stu-id="92fc8-125">Security-neutral code does nothing explicit with the security system.</span></span> <span data-ttu-id="92fc8-126">它會使用接收到的任何使用權限來執行。</span><span class="sxs-lookup"><span data-stu-id="92fc8-126">It runs with whatever permissions it receives.</span></span> <span data-ttu-id="92fc8-127">雖然當應用程式無法攔截與受保護作業 (例如使用檔案、網路等) 關聯的安全性例外狀況時，可能會導致無法處理的例外狀況，安全性中性的程式碼仍然可以利用 .NET Framework 安全性技術。</span><span class="sxs-lookup"><span data-stu-id="92fc8-127">Although applications that fail to catch security exceptions associated with protected operations (such as using files, networking, and so on) can result in an unhandled exception, security-neutral code still takes advantage of the .NET Framework security technologies.</span></span>  
  
 <span data-ttu-id="92fc8-128">安全性中性程式庫具有您須了解的特殊特性。</span><span class="sxs-lookup"><span data-stu-id="92fc8-128">A security-neutral library has special characteristics that you should understand.</span></span> <span data-ttu-id="92fc8-129">假設您的程式庫提供使用檔案或呼叫 Unmanaged 程式碼的 API 項目；如說明所述，如果您的程式碼沒有對應的使用權限，它就不會執行。</span><span class="sxs-lookup"><span data-stu-id="92fc8-129">Suppose your library provides API elements that use files or call unmanaged code; if your code does not have the corresponding permission, it will not run as described.</span></span> <span data-ttu-id="92fc8-130">然而，即使程式碼擁有使用權限，呼叫它的任何應用程式程式碼也必須要有相同的使用權限才能運作。</span><span class="sxs-lookup"><span data-stu-id="92fc8-130">However, even if the code has the permission, any application code that calls it must have the same permission in order to work.</span></span> <span data-ttu-id="92fc8-131">如果呼叫程式碼沒有正確的使用權限<xref:System.Security.SecurityException>出現程式碼存取安全性堆疊查核行程。</span><span class="sxs-lookup"><span data-stu-id="92fc8-131">If the calling code does not have the right permission, a <xref:System.Security.SecurityException> appears as a result of the code access security stack walk.</span></span>  
  
## <a name="application-code-that-is-not-a-reusable-component"></a><span data-ttu-id="92fc8-132">不是重複使用元件的應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="92fc8-132">Application Code That Is Not a Reusable Component</span></span>  
 <span data-ttu-id="92fc8-133">如果您的程式碼所屬的應用程式不會被其他程式碼呼叫，安全性的維護便十分簡單，而且可能不需要撰寫特殊的程式碼。</span><span class="sxs-lookup"><span data-stu-id="92fc8-133">If your code is part of an application that will not be called by other code, security is simple and special coding might not be required.</span></span> <span data-ttu-id="92fc8-134">不過請記住，惡意程式碼可以呼叫您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="92fc8-134">However, remember that malicious code can call your code.</span></span> <span data-ttu-id="92fc8-135">雖然程式碼存取安全性可以制止惡意程式碼存取資源，這類的程式碼還是可以讀取可能含有敏感資訊的欄位或屬性的值。</span><span class="sxs-lookup"><span data-stu-id="92fc8-135">While code access security might stop malicious code from accessing resources, such code could still read values of your fields or properties that might contain sensitive information.</span></span>  
  
 <span data-ttu-id="92fc8-136">此外，如果您的程式碼接受網際網路或其他不可靠來源的使用者輸入，您也必須小心惡意輸入。</span><span class="sxs-lookup"><span data-stu-id="92fc8-136">Additionally, if your code accepts user input from the Internet or other unreliable sources, you must be careful about malicious input.</span></span>  
  
## <a name="managed-wrapper-to-native-code-implementation"></a><span data-ttu-id="92fc8-137">機器碼實作的 Managed 包裝函式</span><span class="sxs-lookup"><span data-stu-id="92fc8-137">Managed Wrapper to Native Code Implementation</span></span>  
 <span data-ttu-id="92fc8-138">在這個案例中，通常某些有用的功能是在您想提供給 Managed 程式碼的機器碼中所實作。</span><span class="sxs-lookup"><span data-stu-id="92fc8-138">Typically in this scenario, some useful functionality is implemented in native code that you want to make available to managed code.</span></span> <span data-ttu-id="92fc8-139">使用平台叫用或 COM Interop 就可輕鬆撰寫 Managed 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="92fc8-139">Managed wrappers are easy to write using either platform invoke or COM interop.</span></span> <span data-ttu-id="92fc8-140">但是，如果您這麼做，包裝函式的呼叫端就必須具有 Unmanaged 程式碼的權限才會成功。</span><span class="sxs-lookup"><span data-stu-id="92fc8-140">However, if you do this, callers of your wrappers must have unmanaged code rights in order to succeed.</span></span> <span data-ttu-id="92fc8-141">在預設原則中，這表示從內部網路或網際網路下載的程式碼將無法使用包裝函式。</span><span class="sxs-lookup"><span data-stu-id="92fc8-141">Under default policy, this means that code downloaded from an intranet or the Internet will not work with the wrappers.</span></span>  
  
 <span data-ttu-id="92fc8-142">比較好的作法是將 Unmanaged 程式碼權限授與包裝函式程式碼，而不是將這些權限授與使用這些包裝函式的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="92fc8-142">Instead of giving all applications that use these wrappers unmanaged code rights, it is better to give these rights only to the wrapper code.</span></span> <span data-ttu-id="92fc8-143">如果基礎功能未公開任何資源而且實作也一樣安全，包裝函式就只需要判斷它的權限，讓任何程式碼都可以透過它來呼叫。</span><span class="sxs-lookup"><span data-stu-id="92fc8-143">If the underlying functionality exposes no resources and the implementation is likewise safe, the wrapper only needs to assert its rights, which enables any code to call through it.</span></span> <span data-ttu-id="92fc8-144">當牽涉到資源時，安全性程式碼撰寫應該與下一章節說明的程式庫程式碼的狀況相同。</span><span class="sxs-lookup"><span data-stu-id="92fc8-144">When resources are involved, security coding should be the same as the library code case described in the next section.</span></span> <span data-ttu-id="92fc8-145">由於包裝函式對這些資源而言是可能公開的呼叫端，因此小心驗證機器碼安全性的程序是必要的，而且這個程序必須由包裝函式負責執行。</span><span class="sxs-lookup"><span data-stu-id="92fc8-145">Because the wrapper is potentially exposing callers to these resources, careful verification of the safety of the native code is necessary and is the wrapper's responsibility.</span></span>  
  
## <a name="library-code-that-exposes-protected-resources"></a><span data-ttu-id="92fc8-146">公開受保護資源的程式庫程式碼</span><span class="sxs-lookup"><span data-stu-id="92fc8-146">Library Code That Exposes Protected Resources</span></span>  
 <span data-ttu-id="92fc8-147">這是安全性程式碼撰寫最具威力的方法，因此也具有潛在的危險 (如果誤用的話)：將您的程式庫當做其他程式碼存取某些特定資源的介面 (如果使用其他方法就無法使用這些資源)，就如同 .NET Framework 的類別對它們使用的資源強制使用權限一般。</span><span class="sxs-lookup"><span data-stu-id="92fc8-147">This is the most powerful and hence potentially dangerous (if done incorrectly) approach for security coding: Your library serves as an interface for other code to access certain resources that are not otherwise available, just as the classes of the .NET Framework enforce permissions for the resources they use.</span></span> <span data-ttu-id="92fc8-148">不論您在何處公開資源，您的程式都必須先要求適用於資源的使用權限 (亦即它必須執行安全性檢查)，然後再判斷它的權限，以執行實際的作業。</span><span class="sxs-lookup"><span data-stu-id="92fc8-148">Wherever you expose a resource, your code must first demand the permission appropriate to the resource (that is, it must perform a security check) and then typically assert its rights to perform the actual operation.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="92fc8-149">相關主題</span><span class="sxs-lookup"><span data-stu-id="92fc8-149">Related Topics</span></span>  
  
|<span data-ttu-id="92fc8-150">標題</span><span class="sxs-lookup"><span data-stu-id="92fc8-150">Title</span></span>|<span data-ttu-id="92fc8-151">描述</span><span class="sxs-lookup"><span data-stu-id="92fc8-151">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="92fc8-152">設定狀態資料的安全性</span><span class="sxs-lookup"><span data-stu-id="92fc8-152">Securing State Data</span></span>](../../../docs/standard/security/securing-state-data.md)|<span data-ttu-id="92fc8-153">說明如何保護私用成員。</span><span class="sxs-lookup"><span data-stu-id="92fc8-153">Describes how to protect private members.</span></span>|  
|[<span data-ttu-id="92fc8-154">安全性和使用者輸入</span><span class="sxs-lookup"><span data-stu-id="92fc8-154">Security and User Input</span></span>](../../../docs/standard/security/security-and-user-input.md)|<span data-ttu-id="92fc8-155">描述接受使用者輸入之應用程式的安全性疑慮。</span><span class="sxs-lookup"><span data-stu-id="92fc8-155">Describes security concerns for applications that accept user input.</span></span>|  
|[<span data-ttu-id="92fc8-156">安全性和競爭情形</span><span class="sxs-lookup"><span data-stu-id="92fc8-156">Security and Race Conditions</span></span>](../../../docs/standard/security/security-and-race-conditions.md)|<span data-ttu-id="92fc8-157">說明如何避免程式碼中的競爭情形。</span><span class="sxs-lookup"><span data-stu-id="92fc8-157">Describes how to avoid race conditions in your code.</span></span>|  
|[<span data-ttu-id="92fc8-158">安全性和產生作業中的程式碼</span><span class="sxs-lookup"><span data-stu-id="92fc8-158">Security and On-the-Fly Code Generation</span></span>](../../../docs/standard/security/security-and-on-the-fly-code-generation.md)|<span data-ttu-id="92fc8-159">描述產生動態程式碼之應用程式的安全性疑慮。</span><span class="sxs-lookup"><span data-stu-id="92fc8-159">Describes security concerns for applications that generate dynamic code.</span></span>|  
|[<span data-ttu-id="92fc8-160">以角色為基礎的安全性</span><span class="sxs-lookup"><span data-stu-id="92fc8-160">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)|<span data-ttu-id="92fc8-161">詳細描述 .NET Framework 以角色為基礎的安全性，並提供將它用於您的程式碼中的指示。</span><span class="sxs-lookup"><span data-stu-id="92fc8-161">Describes .NET Framework role-based security in detail and provides instructions for using it in your code.</span></span>|
