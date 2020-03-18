---
title: 保護 .NET 的編碼準則
description: 設計要使用的代碼。NET 強制許可權和其他強制，以説明防止惡意程式碼訪問資料或執行其他操作。
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
ms.openlocfilehash: 05f7e039ecdc0cd33baa015872924fb9e1f078aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187720"
---
# <a name="secure-coding-guidelines"></a><span data-ttu-id="1ce17-103">安全編碼指南</span><span class="sxs-lookup"><span data-stu-id="1ce17-103">Secure coding guidelines</span></span>

<span data-ttu-id="1ce17-104">辨識項架構的安全性和程式碼存取安全性提供十分強大的明確機制以實作安全性。</span><span class="sxs-lookup"><span data-stu-id="1ce17-104">Evidence-based security and code access security provide very powerful, explicit mechanisms to implement security.</span></span> <span data-ttu-id="1ce17-105">大多數應用程式代碼只能使用 .NET 實現的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="1ce17-105">Most application code can simply use the infrastructure implemented by .NET.</span></span> <span data-ttu-id="1ce17-106">某些情況還需要其他的應用程式特定安全性 (藉由擴充安全性系統或是使用新的臨機操作方法來建置)。</span><span class="sxs-lookup"><span data-stu-id="1ce17-106">In some cases, additional application-specific security is required, built either by extending the security system or by using new ad hoc methods.</span></span>

<span data-ttu-id="1ce17-107">在代碼中使用 .NET 強制許可權和其他強制，應設置障礙，以防止惡意程式碼訪問不希望其擁有的資訊或執行其他不可取的操作。</span><span class="sxs-lookup"><span data-stu-id="1ce17-107">Using .NET enforced permissions and other enforcement in your code, you should erect barriers to prevent malicious code from accessing information that you don't want it to have or performing other undesirable actions.</span></span> <span data-ttu-id="1ce17-108">此外，在所有使用受信任程式碼的可預期案例中，您必須在安全性與可用性之間達成平衡。</span><span class="sxs-lookup"><span data-stu-id="1ce17-108">Additionally, you must strike a balance between security and usability in all the expected scenarios using trusted code.</span></span>

<span data-ttu-id="1ce17-109">本概觀說明設計程式碼以搭配使用安全性系統時，可以採用的不同方式。</span><span class="sxs-lookup"><span data-stu-id="1ce17-109">This overview describes the different ways code can be designed to work with the security system.</span></span>

## <a name="securing-resource-access"></a><span data-ttu-id="1ce17-110">保護資源訪問</span><span class="sxs-lookup"><span data-stu-id="1ce17-110">Securing resource access</span></span>

<span data-ttu-id="1ce17-111">當設計和撰寫程式碼時，您需要保護並限制程式碼對資源的存取，特別是當使用或叫用未知來源的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="1ce17-111">When designing and writing your code, you need to protect and limit the access that code has to resources, especially when using or invoking code of unknown origin.</span></span> <span data-ttu-id="1ce17-112">因此，請牢記下列技術，以確保程式碼是安全的︰</span><span class="sxs-lookup"><span data-stu-id="1ce17-112">So, keep in mind the following techniques to ensure your code is secure:</span></span>

- <span data-ttu-id="1ce17-113">請勿使用程式碼存取安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="1ce17-113">Do not use Code Access Security (CAS).</span></span>

- <span data-ttu-id="1ce17-114">請勿使用部分信任程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ce17-114">Do not use partial trusted code.</span></span>

- <span data-ttu-id="1ce17-115">不要使用["允許部分受信任的調用方"](xref:System.Security.AllowPartiallyTrustedCallersAttribute)屬性 （APTCA）。</span><span class="sxs-lookup"><span data-stu-id="1ce17-115">Do not use the [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) attribute (APTCA).</span></span>

- <span data-ttu-id="1ce17-116">請勿使用 .NET 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="1ce17-116">Do not use .NET Remoting.</span></span>

- <span data-ttu-id="1ce17-117">請勿使用分散式元件物件模型 (DCOM)。</span><span class="sxs-lookup"><span data-stu-id="1ce17-117">Do not use Distributed Component Object Model (DCOM).</span></span>

- <span data-ttu-id="1ce17-118">請勿使用二進位格式器。</span><span class="sxs-lookup"><span data-stu-id="1ce17-118">Do not use binary formatters.</span></span>

<span data-ttu-id="1ce17-119">代碼訪問安全和安全透明代碼不支援作為具有部分受信任代碼的安全邊界。</span><span class="sxs-lookup"><span data-stu-id="1ce17-119">Code Access Security and Security-Transparent Code are not supported as a security boundary with partially trusted code.</span></span> <span data-ttu-id="1ce17-120">建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。</span><span class="sxs-lookup"><span data-stu-id="1ce17-120">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="1ce17-121">替代的安全性措施包括︰</span><span class="sxs-lookup"><span data-stu-id="1ce17-121">The alternative security measures are:</span></span>

- <span data-ttu-id="1ce17-122">虛擬化</span><span class="sxs-lookup"><span data-stu-id="1ce17-122">Virtualization</span></span>

- <span data-ttu-id="1ce17-123">AppContainers</span><span class="sxs-lookup"><span data-stu-id="1ce17-123">AppContainers</span></span>

- <span data-ttu-id="1ce17-124">作業系統 (OS) 使用者和權限</span><span class="sxs-lookup"><span data-stu-id="1ce17-124">Operating system (OS) users and permissions</span></span>

- <span data-ttu-id="1ce17-125">Hyper-V 容器</span><span class="sxs-lookup"><span data-stu-id="1ce17-125">Hyper-V containers</span></span>

## <a name="security-neutral-code"></a><span data-ttu-id="1ce17-126">安全中立代碼</span><span class="sxs-lookup"><span data-stu-id="1ce17-126">Security-neutral code</span></span>

<span data-ttu-id="1ce17-127">安全性中性的程式碼與安全性系統並無明顯關聯。</span><span class="sxs-lookup"><span data-stu-id="1ce17-127">Security-neutral code does nothing explicit with the security system.</span></span> <span data-ttu-id="1ce17-128">它會使用接收到的任何使用權限來執行。</span><span class="sxs-lookup"><span data-stu-id="1ce17-128">It runs with whatever permissions it receives.</span></span> <span data-ttu-id="1ce17-129">儘管無法捕獲與受保護操作（如使用檔、網路等）關聯的安全異常的應用程式可能會導致未處理的異常，但安全中立代碼仍利用 .NET 中的安全技術.</span><span class="sxs-lookup"><span data-stu-id="1ce17-129">Although applications that fail to catch security exceptions associated with protected operations (such as using files, networking, and so on) can result in an unhandled exception, security-neutral code still takes advantage of the security technologies in .NET.</span></span>

<span data-ttu-id="1ce17-130">安全性中性程式庫具有您須了解的特殊特性。</span><span class="sxs-lookup"><span data-stu-id="1ce17-130">A security-neutral library has special characteristics that you should understand.</span></span> <span data-ttu-id="1ce17-131">假設您的庫提供使用檔或調用非託管代碼的 API 元素。</span><span class="sxs-lookup"><span data-stu-id="1ce17-131">Suppose your library provides API elements that use files or call unmanaged code.</span></span> <span data-ttu-id="1ce17-132">如果代碼沒有相應的許可權，則代碼不會按照所述運行。</span><span class="sxs-lookup"><span data-stu-id="1ce17-132">If your code doesn't have the corresponding permission, it won't run as described.</span></span> <span data-ttu-id="1ce17-133">然而，即使程式碼擁有使用權限，呼叫它的任何應用程式程式碼也必須要有相同的使用權限才能運作。</span><span class="sxs-lookup"><span data-stu-id="1ce17-133">However, even if the code has the permission, any application code that calls it must have the same permission in order to work.</span></span> <span data-ttu-id="1ce17-134">如果調用代碼沒有正確的許可權，則 作為代碼訪問安全<xref:System.Security.SecurityException>堆疊遍歷的結果將出現 。</span><span class="sxs-lookup"><span data-stu-id="1ce17-134">If the calling code doesn't have the right permission, a <xref:System.Security.SecurityException> appears as a result of the code access security stack walk.</span></span>

## <a name="application-code-that-isnt-a-reusable-component"></a><span data-ttu-id="1ce17-135">不是可重用元件的應用程式代碼</span><span class="sxs-lookup"><span data-stu-id="1ce17-135">Application code that isn't a reusable component</span></span>

<span data-ttu-id="1ce17-136">如果代碼是其他代碼不會調用的應用程式的一部分，則安全性很簡單，並且可能不需要特殊編碼。</span><span class="sxs-lookup"><span data-stu-id="1ce17-136">If your code is part of an application that won't be called by other code, security is simple and special coding might not be required.</span></span> <span data-ttu-id="1ce17-137">不過請記住，惡意程式碼可以呼叫您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ce17-137">However, remember that malicious code can call your code.</span></span> <span data-ttu-id="1ce17-138">雖然程式碼存取安全性可以制止惡意程式碼存取資源，這類的程式碼還是可以讀取可能含有敏感資訊的欄位或屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1ce17-138">While code access security might stop malicious code from accessing resources, such code could still read values of your fields or properties that might contain sensitive information.</span></span>

<span data-ttu-id="1ce17-139">此外，如果您的程式碼接受網際網路或其他不可靠來源的使用者輸入，您也必須小心惡意輸入。</span><span class="sxs-lookup"><span data-stu-id="1ce17-139">Additionally, if your code accepts user input from the Internet or other unreliable sources, you must be careful about malicious input.</span></span>

## <a name="managed-wrapper-to-native-code-implementation"></a><span data-ttu-id="1ce17-140">託管包裝到本機代碼實現</span><span class="sxs-lookup"><span data-stu-id="1ce17-140">Managed wrapper to native code implementation</span></span>

<span data-ttu-id="1ce17-141">在這個案例中，通常某些有用的功能是在您想提供給 Managed 程式碼的機器碼中所實作。</span><span class="sxs-lookup"><span data-stu-id="1ce17-141">Typically in this scenario, some useful functionality is implemented in native code that you want to make available to managed code.</span></span> <span data-ttu-id="1ce17-142">使用平台叫用或 COM Interop 就可輕鬆撰寫 Managed 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="1ce17-142">Managed wrappers are easy to write using either platform invoke or COM interop.</span></span> <span data-ttu-id="1ce17-143">但是，如果您這麼做，包裝函式的呼叫端就必須具有 Unmanaged 程式碼的權限才會成功。</span><span class="sxs-lookup"><span data-stu-id="1ce17-143">However, if you do this, callers of your wrappers must have unmanaged code rights in order to succeed.</span></span> <span data-ttu-id="1ce17-144">在預設策略下，這意味著從 Intranet 或 Internet 下載的代碼將不能與包裝器配合使用。</span><span class="sxs-lookup"><span data-stu-id="1ce17-144">Under default policy, this means that code downloaded from an intranet or the Internet won't work with the wrappers.</span></span>

<span data-ttu-id="1ce17-145">與其將非託管代碼許可權授予使用這些包裝器的所有應用程式，不如僅將這些許可權授予包裝代碼。</span><span class="sxs-lookup"><span data-stu-id="1ce17-145">Instead of giving unmanaged code rights to all applications that use these wrappers, it's better to give these rights only to the wrapper code.</span></span> <span data-ttu-id="1ce17-146">如果基礎功能未公開任何資源而且實作也一樣安全，包裝函式就只需要判斷它的權限，讓任何程式碼都可以透過它來呼叫。</span><span class="sxs-lookup"><span data-stu-id="1ce17-146">If the underlying functionality exposes no resources and the implementation is likewise safe, the wrapper only needs to assert its rights, which enables any code to call through it.</span></span> <span data-ttu-id="1ce17-147">當牽涉到資源時，安全性程式碼撰寫應該與下一章節說明的程式庫程式碼的狀況相同。</span><span class="sxs-lookup"><span data-stu-id="1ce17-147">When resources are involved, security coding should be the same as the library code case described in the next section.</span></span> <span data-ttu-id="1ce17-148">由於包裝函式對這些資源而言是可能公開的呼叫端，因此小心驗證機器碼安全性的程序是必要的，而且這個程序必須由包裝函式負責執行。</span><span class="sxs-lookup"><span data-stu-id="1ce17-148">Because the wrapper is potentially exposing callers to these resources, careful verification of the safety of the native code is necessary and is the wrapper's responsibility.</span></span>

## <a name="library-code-that-exposes-protected-resources"></a><span data-ttu-id="1ce17-149">公開受保護資源的庫代碼</span><span class="sxs-lookup"><span data-stu-id="1ce17-149">Library code that exposes protected resources</span></span>

<span data-ttu-id="1ce17-150">以下方法是安全編碼最強大且具有潛在危險（如果處理不正確）：您的庫充當其他代碼訪問某些不可用資源的介面，就像 .NET 類強制他們使用的資源的許可權。</span><span class="sxs-lookup"><span data-stu-id="1ce17-150">The following approach is the most powerful and hence potentially dangerous (if done incorrectly) for security coding: your library serves as an interface for other code to access certain resources that aren't otherwise available, just as the .NET classes enforce permissions for the resources they use.</span></span> <span data-ttu-id="1ce17-151">不論您在何處公開資源，您的程式都必須先要求適用於資源的使用權限 (亦即它必須執行安全性檢查)，然後再判斷它的權限，以執行實際的作業。</span><span class="sxs-lookup"><span data-stu-id="1ce17-151">Wherever you expose a resource, your code must first demand the permission appropriate to the resource (that is, it must perform a security check) and then typically assert its rights to perform the actual operation.</span></span>

## <a name="related-topics"></a><span data-ttu-id="1ce17-152">相關主題</span><span class="sxs-lookup"><span data-stu-id="1ce17-152">Related topics</span></span>

|<span data-ttu-id="1ce17-153">Title</span><span class="sxs-lookup"><span data-stu-id="1ce17-153">Title</span></span>|<span data-ttu-id="1ce17-154">描述</span><span class="sxs-lookup"><span data-stu-id="1ce17-154">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="1ce17-155">設定狀態資料的安全性</span><span class="sxs-lookup"><span data-stu-id="1ce17-155">Securing State Data</span></span>](securing-state-data.md)|<span data-ttu-id="1ce17-156">說明如何保護私用成員。</span><span class="sxs-lookup"><span data-stu-id="1ce17-156">Describes how to protect private members.</span></span>|
|[<span data-ttu-id="1ce17-157">安全性和使用者輸入</span><span class="sxs-lookup"><span data-stu-id="1ce17-157">Security and User Input</span></span>](security-and-user-input.md)|<span data-ttu-id="1ce17-158">描述接受使用者輸入之應用程式的安全性疑慮。</span><span class="sxs-lookup"><span data-stu-id="1ce17-158">Describes security concerns for applications that accept user input.</span></span>|
|[<span data-ttu-id="1ce17-159">安全性和競爭情形</span><span class="sxs-lookup"><span data-stu-id="1ce17-159">Security and Race Conditions</span></span>](security-and-race-conditions.md)|<span data-ttu-id="1ce17-160">說明如何避免程式碼中的競爭情形。</span><span class="sxs-lookup"><span data-stu-id="1ce17-160">Describes how to avoid race conditions in your code.</span></span>|
|[<span data-ttu-id="1ce17-161">安全性和產生作業中的程式碼</span><span class="sxs-lookup"><span data-stu-id="1ce17-161">Security and On-the-Fly Code Generation</span></span>](security-and-on-the-fly-code-generation.md)|<span data-ttu-id="1ce17-162">描述產生動態程式碼之應用程式的安全性疑慮。</span><span class="sxs-lookup"><span data-stu-id="1ce17-162">Describes security concerns for applications that generate dynamic code.</span></span>|
|[<span data-ttu-id="1ce17-163">基於角色的安全性</span><span class="sxs-lookup"><span data-stu-id="1ce17-163">Role-Based Security</span></span>](role-based-security.md)|<span data-ttu-id="1ce17-164">詳細介紹了基於 .NET 角色的安全性，並提供了在代碼中使用它的說明。</span><span class="sxs-lookup"><span data-stu-id="1ce17-164">Describes .NET role-based security in detail and provides instructions for using it in your code.</span></span>|
