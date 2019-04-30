---
title: .NET 的安全編碼指南
ms.date: 06/28/2018
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3a8f0dfc1a2b5e09722876b73281ed1d8b6334e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018641"
---
# <a name="secure-coding-guidelines"></a><span data-ttu-id="dbb14-102">安全編碼指南</span><span class="sxs-lookup"><span data-stu-id="dbb14-102">Secure coding guidelines</span></span>

<span data-ttu-id="dbb14-103">辨識項架構的安全性和程式碼存取安全性提供十分強大的明確機制以實作安全性。</span><span class="sxs-lookup"><span data-stu-id="dbb14-103">Evidence-based security and code access security provide very powerful, explicit mechanisms to implement security.</span></span> <span data-ttu-id="dbb14-104">大部分的應用程式程式碼可以直接使用由.NET 實作的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="dbb14-104">Most application code can simply use the infrastructure implemented by .NET.</span></span> <span data-ttu-id="dbb14-105">某些情況還需要其他的應用程式特定安全性 (藉由擴充安全性系統或是使用新的臨機操作方法來建置)。</span><span class="sxs-lookup"><span data-stu-id="dbb14-105">In some cases, additional application-specific security is required, built either by extending the security system or by using new ad hoc methods.</span></span>

<span data-ttu-id="dbb14-106">使用.NET 強制執行權限和其他強制程式碼中的，您應該可以設置防線來防止惡意程式碼存取，您不想要有的資訊或執行其他不當動作。</span><span class="sxs-lookup"><span data-stu-id="dbb14-106">Using .NET enforced permissions and other enforcement in your code, you should erect barriers to prevent malicious code from accessing information that you don't want it to have or performing other undesirable actions.</span></span> <span data-ttu-id="dbb14-107">此外，在所有使用受信任程式碼的可預期案例中，您必須在安全性與可用性之間達成平衡。</span><span class="sxs-lookup"><span data-stu-id="dbb14-107">Additionally, you must strike a balance between security and usability in all the expected scenarios using trusted code.</span></span>

<span data-ttu-id="dbb14-108">本概觀說明設計程式碼以搭配使用安全性系統時，可以採用的不同方式。</span><span class="sxs-lookup"><span data-stu-id="dbb14-108">This overview describes the different ways code can be designed to work with the security system.</span></span>

## <a name="securing-resource-access"></a><span data-ttu-id="dbb14-109">保護資源存取</span><span class="sxs-lookup"><span data-stu-id="dbb14-109">Securing resource access</span></span>

<span data-ttu-id="dbb14-110">當設計和撰寫程式碼時，您需要保護並限制程式碼對資源的存取，特別是當使用或叫用未知來源的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="dbb14-110">When designing and writing your code, you need to protect and limit the access that code has to resources, especially when using or invoking code of unknown origin.</span></span> <span data-ttu-id="dbb14-111">因此，請牢記下列技術，以確保程式碼是安全的︰</span><span class="sxs-lookup"><span data-stu-id="dbb14-111">So, keep in mind the following techniques to ensure your code is secure:</span></span>

- <span data-ttu-id="dbb14-112">請勿使用程式碼存取安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="dbb14-112">Do not use Code Access Security (CAS).</span></span>

- <span data-ttu-id="dbb14-113">請勿使用部分信任程式碼。</span><span class="sxs-lookup"><span data-stu-id="dbb14-113">Do not use partial trusted code.</span></span>

- <span data-ttu-id="dbb14-114">請勿使用[AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute)屬性 (APTCA)。</span><span class="sxs-lookup"><span data-stu-id="dbb14-114">Do not use the [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) attribute (APTCA).</span></span>

- <span data-ttu-id="dbb14-115">請勿使用 .NET 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="dbb14-115">Do not use .NET Remoting.</span></span>

- <span data-ttu-id="dbb14-116">請勿使用分散式元件物件模型 (DCOM)。</span><span class="sxs-lookup"><span data-stu-id="dbb14-116">Do not use Distributed Component Object Model (DCOM).</span></span>

- <span data-ttu-id="dbb14-117">請勿使用二進位格式器。</span><span class="sxs-lookup"><span data-stu-id="dbb14-117">Do not use binary formatters.</span></span>

<span data-ttu-id="dbb14-118">不支援程式碼存取安全性和安全性透明程式碼做為部分信任程式碼與安全性界限。</span><span class="sxs-lookup"><span data-stu-id="dbb14-118">Code Access Security and Security-Transparent Code are not supported as a security boundary with partially trusted code.</span></span> <span data-ttu-id="dbb14-119">建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。</span><span class="sxs-lookup"><span data-stu-id="dbb14-119">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="dbb14-120">替代的安全性措施包括︰</span><span class="sxs-lookup"><span data-stu-id="dbb14-120">The alternative security measures are:</span></span>

- <span data-ttu-id="dbb14-121">虛擬化</span><span class="sxs-lookup"><span data-stu-id="dbb14-121">Virtualization</span></span>

- <span data-ttu-id="dbb14-122">AppContainers</span><span class="sxs-lookup"><span data-stu-id="dbb14-122">AppContainers</span></span>

- <span data-ttu-id="dbb14-123">作業系統 (OS) 使用者和權限</span><span class="sxs-lookup"><span data-stu-id="dbb14-123">Operating system (OS) users and permissions</span></span>

- <span data-ttu-id="dbb14-124">Hyper-V 容器</span><span class="sxs-lookup"><span data-stu-id="dbb14-124">Hyper-V containers</span></span>

## <a name="security-neutral-code"></a><span data-ttu-id="dbb14-125">安全性中性的程式碼</span><span class="sxs-lookup"><span data-stu-id="dbb14-125">Security-neutral code</span></span>

<span data-ttu-id="dbb14-126">安全性中性的程式碼與安全性系統並無明顯關聯。</span><span class="sxs-lookup"><span data-stu-id="dbb14-126">Security-neutral code does nothing explicit with the security system.</span></span> <span data-ttu-id="dbb14-127">它會使用接收到的任何使用權限來執行。</span><span class="sxs-lookup"><span data-stu-id="dbb14-127">It runs with whatever permissions it receives.</span></span> <span data-ttu-id="dbb14-128">安全性中性的程式碼雖然無法攔截與受保護的作業 （例如使用檔案、 網路等等） 相關聯的安全性例外狀況的應用程式可能會導致未處理的例外狀況，仍會在.NET 中充分利用的安全性技術.</span><span class="sxs-lookup"><span data-stu-id="dbb14-128">Although applications that fail to catch security exceptions associated with protected operations (such as using files, networking, and so on) can result in an unhandled exception, security-neutral code still takes advantage of the security technologies in .NET.</span></span>

<span data-ttu-id="dbb14-129">安全性中性程式庫具有您須了解的特殊特性。</span><span class="sxs-lookup"><span data-stu-id="dbb14-129">A security-neutral library has special characteristics that you should understand.</span></span> <span data-ttu-id="dbb14-130">假設您的程式庫提供使用檔案或呼叫 unmanaged 程式碼的 API 項目。</span><span class="sxs-lookup"><span data-stu-id="dbb14-130">Suppose your library provides API elements that use files or call unmanaged code.</span></span> <span data-ttu-id="dbb14-131">如果您的程式碼沒有對應的權限，它將不會執行所述。</span><span class="sxs-lookup"><span data-stu-id="dbb14-131">If your code doesn't have the corresponding permission, it won't run as described.</span></span> <span data-ttu-id="dbb14-132">然而，即使程式碼擁有使用權限，呼叫它的任何應用程式程式碼也必須要有相同的使用權限才能運作。</span><span class="sxs-lookup"><span data-stu-id="dbb14-132">However, even if the code has the permission, any application code that calls it must have the same permission in order to work.</span></span> <span data-ttu-id="dbb14-133">如果呼叫程式碼沒有正確的權限，<xref:System.Security.SecurityException>出現程式碼存取安全性堆疊查核行程。</span><span class="sxs-lookup"><span data-stu-id="dbb14-133">If the calling code doesn't have the right permission, a <xref:System.Security.SecurityException> appears as a result of the code access security stack walk.</span></span>

## <a name="application-code-that-isnt-a-reusable-component"></a><span data-ttu-id="dbb14-134">不是可重複使用元件的應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="dbb14-134">Application code that isn't a reusable component</span></span>

<span data-ttu-id="dbb14-135">如果您的程式碼是不會由其他程式碼呼叫的應用程式的一部分，安全性很簡單，以及特殊的程式碼可能不需要。</span><span class="sxs-lookup"><span data-stu-id="dbb14-135">If your code is part of an application that won't be called by other code, security is simple and special coding might not be required.</span></span> <span data-ttu-id="dbb14-136">不過請記住，惡意程式碼可以呼叫您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dbb14-136">However, remember that malicious code can call your code.</span></span> <span data-ttu-id="dbb14-137">雖然程式碼存取安全性可以制止惡意程式碼存取資源，這類的程式碼還是可以讀取可能含有敏感資訊的欄位或屬性的值。</span><span class="sxs-lookup"><span data-stu-id="dbb14-137">While code access security might stop malicious code from accessing resources, such code could still read values of your fields or properties that might contain sensitive information.</span></span>

<span data-ttu-id="dbb14-138">此外，如果您的程式碼接受網際網路或其他不可靠來源的使用者輸入，您也必須小心惡意輸入。</span><span class="sxs-lookup"><span data-stu-id="dbb14-138">Additionally, if your code accepts user input from the Internet or other unreliable sources, you must be careful about malicious input.</span></span>

## <a name="managed-wrapper-to-native-code-implementation"></a><span data-ttu-id="dbb14-139">Managed 包裝函式原生程式碼實作</span><span class="sxs-lookup"><span data-stu-id="dbb14-139">Managed wrapper to native code implementation</span></span>

<span data-ttu-id="dbb14-140">在這個案例中，通常某些有用的功能是在您想提供給 Managed 程式碼的機器碼中所實作。</span><span class="sxs-lookup"><span data-stu-id="dbb14-140">Typically in this scenario, some useful functionality is implemented in native code that you want to make available to managed code.</span></span> <span data-ttu-id="dbb14-141">使用平台叫用或 COM Interop 就可輕鬆撰寫 Managed 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="dbb14-141">Managed wrappers are easy to write using either platform invoke or COM interop.</span></span> <span data-ttu-id="dbb14-142">但是，如果您這麼做，包裝函式的呼叫端就必須具有 Unmanaged 程式碼的權限才會成功。</span><span class="sxs-lookup"><span data-stu-id="dbb14-142">However, if you do this, callers of your wrappers must have unmanaged code rights in order to succeed.</span></span> <span data-ttu-id="dbb14-143">依照預設原則，這表示來自內部網路下載的程式碼，或網際網路不會使用包裝函式。</span><span class="sxs-lookup"><span data-stu-id="dbb14-143">Under default policy, this means that code downloaded from an intranet or the Internet won't work with the wrappers.</span></span>

<span data-ttu-id="dbb14-144">不會給 unmanaged 程式碼使用這些包裝函式的所有應用程式的權限，最好是讓這些權限給包裝函式程式碼。</span><span class="sxs-lookup"><span data-stu-id="dbb14-144">Instead of giving unmanaged code rights to all applications that use these wrappers, it's better to give these rights only to the wrapper code.</span></span> <span data-ttu-id="dbb14-145">如果基礎功能未公開任何資源而且實作也一樣安全，包裝函式就只需要判斷它的權限，讓任何程式碼都可以透過它來呼叫。</span><span class="sxs-lookup"><span data-stu-id="dbb14-145">If the underlying functionality exposes no resources and the implementation is likewise safe, the wrapper only needs to assert its rights, which enables any code to call through it.</span></span> <span data-ttu-id="dbb14-146">當牽涉到資源時，安全性程式碼撰寫應該與下一章節說明的程式庫程式碼的狀況相同。</span><span class="sxs-lookup"><span data-stu-id="dbb14-146">When resources are involved, security coding should be the same as the library code case described in the next section.</span></span> <span data-ttu-id="dbb14-147">由於包裝函式對這些資源而言是可能公開的呼叫端，因此小心驗證機器碼安全性的程序是必要的，而且這個程序必須由包裝函式負責執行。</span><span class="sxs-lookup"><span data-stu-id="dbb14-147">Because the wrapper is potentially exposing callers to these resources, careful verification of the safety of the native code is necessary and is the wrapper's responsibility.</span></span>

## <a name="library-code-that-exposes-protected-resources"></a><span data-ttu-id="dbb14-148">公開 （expose） 的程式庫程式碼受保護的資源</span><span class="sxs-lookup"><span data-stu-id="dbb14-148">Library code that exposes protected resources</span></span>

<span data-ttu-id="dbb14-149">下列的方法是最具威力，因此有潛在危險 （如果誤用） 撰寫程式碼安全性： 您的程式庫做為存取無法否則就如同.NET 類別強制特定資源的其他程式碼的介面使用的資源的權限。</span><span class="sxs-lookup"><span data-stu-id="dbb14-149">The following approach is the most powerful and hence potentially dangerous (if done incorrectly) for security coding: your library serves as an interface for other code to access certain resources that aren't otherwise available, just as the .NET classes enforce permissions for the resources they use.</span></span> <span data-ttu-id="dbb14-150">不論您在何處公開資源，您的程式都必須先要求適用於資源的使用權限 (亦即它必須執行安全性檢查)，然後再判斷它的權限，以執行實際的作業。</span><span class="sxs-lookup"><span data-stu-id="dbb14-150">Wherever you expose a resource, your code must first demand the permission appropriate to the resource (that is, it must perform a security check) and then typically assert its rights to perform the actual operation.</span></span>

## <a name="related-topics"></a><span data-ttu-id="dbb14-151">相關主題</span><span class="sxs-lookup"><span data-stu-id="dbb14-151">Related topics</span></span>

|<span data-ttu-id="dbb14-152">標題</span><span class="sxs-lookup"><span data-stu-id="dbb14-152">Title</span></span>|<span data-ttu-id="dbb14-153">描述</span><span class="sxs-lookup"><span data-stu-id="dbb14-153">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="dbb14-154">設定狀態資料的安全性</span><span class="sxs-lookup"><span data-stu-id="dbb14-154">Securing State Data</span></span>](securing-state-data.md)|<span data-ttu-id="dbb14-155">說明如何保護私用成員。</span><span class="sxs-lookup"><span data-stu-id="dbb14-155">Describes how to protect private members.</span></span>|
|[<span data-ttu-id="dbb14-156">安全性和使用者輸入</span><span class="sxs-lookup"><span data-stu-id="dbb14-156">Security and User Input</span></span>](security-and-user-input.md)|<span data-ttu-id="dbb14-157">描述接受使用者輸入之應用程式的安全性疑慮。</span><span class="sxs-lookup"><span data-stu-id="dbb14-157">Describes security concerns for applications that accept user input.</span></span>|
|[<span data-ttu-id="dbb14-158">安全性和競爭情形</span><span class="sxs-lookup"><span data-stu-id="dbb14-158">Security and Race Conditions</span></span>](security-and-race-conditions.md)|<span data-ttu-id="dbb14-159">說明如何避免程式碼中的競爭情形。</span><span class="sxs-lookup"><span data-stu-id="dbb14-159">Describes how to avoid race conditions in your code.</span></span>|
|[<span data-ttu-id="dbb14-160">安全性和產生作業中的程式碼</span><span class="sxs-lookup"><span data-stu-id="dbb14-160">Security and On-the-Fly Code Generation</span></span>](security-and-on-the-fly-code-generation.md)|<span data-ttu-id="dbb14-161">描述產生動態程式碼之應用程式的安全性疑慮。</span><span class="sxs-lookup"><span data-stu-id="dbb14-161">Describes security concerns for applications that generate dynamic code.</span></span>|
|[<span data-ttu-id="dbb14-162">以角色為基礎的安全性</span><span class="sxs-lookup"><span data-stu-id="dbb14-162">Role-Based Security</span></span>](role-based-security.md)|<span data-ttu-id="dbb14-163">描述.NET 角色型安全性詳細資料，並提供將它用於您的程式碼中的指示。</span><span class="sxs-lookup"><span data-stu-id="dbb14-163">Describes .NET role-based security in detail and provides instructions for using it in your code.</span></span>|
