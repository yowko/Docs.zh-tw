---
title: 限定 COM 互通的 .NET 型別
description: 本文提供的指導方針可協助您將 .NET 元件中的類型公開給 com interop 的 COM 應用程式。
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: 3fa9f0d5d8dd4d532fc510a1d946eddf32016748
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187758"
---
# <a name="qualifying-net-types-for-com-interoperation"></a><span data-ttu-id="1d67b-103">限定 COM 互通的 .NET 型別</span><span class="sxs-lookup"><span data-stu-id="1d67b-103">Qualifying .NET Types for COM Interoperation</span></span>
<span data-ttu-id="1d67b-104">如果您想要向 COM 應用程式公開組件中的類型，請考慮設計階段的 COM Interop 需求。</span><span class="sxs-lookup"><span data-stu-id="1d67b-104">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="1d67b-105">當您遵守下列方針時，Managed 類型 (類別、介面、結構和列舉) 會與 COM 類型緊密整合：</span><span class="sxs-lookup"><span data-stu-id="1d67b-105">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="1d67b-106">類別應該明確地實作介面。</span><span class="sxs-lookup"><span data-stu-id="1d67b-106">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="1d67b-107">雖然 COM Interop 提供機制來自動產生包含類別之所有成員和其基底類別成員的介面，最好是目前提供明確的介面。但是最好是提供明確介面。</span><span class="sxs-lookup"><span data-stu-id="1d67b-107">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="1d67b-108">自動產生的介面稱為類別介面。</span><span class="sxs-lookup"><span data-stu-id="1d67b-108">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="1d67b-109">如需指導方針，請參閱 [類別介面簡介](com-callable-wrapper.md#introducing-the-class-interface)。</span><span class="sxs-lookup"><span data-stu-id="1d67b-109">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="1d67b-110">您可以使用 Visual Basic、C# 和 C++ 在程式碼中併入介面定義，而不需使用介面定義語言 (IDL) 或其對等項目。</span><span class="sxs-lookup"><span data-stu-id="1d67b-110">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="1d67b-111">如需語法詳細資訊，請參閱您的語言文件。</span><span class="sxs-lookup"><span data-stu-id="1d67b-111">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="1d67b-112">Managed 類型必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="1d67b-112">Managed types must be public.</span></span>  
  
     <span data-ttu-id="1d67b-113">只有組件中的公用類型才會註冊並匯出至型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="1d67b-113">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="1d67b-114">因此，只有 COM 才能看到公用類型。</span><span class="sxs-lookup"><span data-stu-id="1d67b-114">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="1d67b-115">Managed 類型會向可能未向 COM 公開的其他 Managed 程式碼公開功能。</span><span class="sxs-lookup"><span data-stu-id="1d67b-115">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="1d67b-116">例如，不會向 COM 用戶端公開參數化建構函式、靜態方法和常數欄位。</span><span class="sxs-lookup"><span data-stu-id="1d67b-116">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="1d67b-117">此外，執行階段將資料封送處理至類型或從中封送處理資料時，可能會複製或轉換資料。</span><span class="sxs-lookup"><span data-stu-id="1d67b-117">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="1d67b-118">方法、屬性、欄位和事件必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="1d67b-118">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="1d67b-119">如果要讓 COM 看到公用類型的成員，則它們也必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="1d67b-119">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="1d67b-120">您可以套用 <xref:System.Runtime.InteropServices.ComVisibleAttribute>，以限制組件、公用類型或公用類型的公用成員的可見性。</span><span class="sxs-lookup"><span data-stu-id="1d67b-120">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="1d67b-121">根據預設，會顯示所有公用類型和成員。</span><span class="sxs-lookup"><span data-stu-id="1d67b-121">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="1d67b-122">型別必須具有要從 COM 啟用的公用無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d67b-122">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="1d67b-123">COM 可以看到 Managed 公用類型。</span><span class="sxs-lookup"><span data-stu-id="1d67b-123">Managed, public types are visible to COM.</span></span> <span data-ttu-id="1d67b-124">不過，若沒有公用無參數建構函式 (沒有引數的建構函式)，COM 用戶端就無法建立該型別。</span><span class="sxs-lookup"><span data-stu-id="1d67b-124">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="1d67b-125">如果該類型是透過一些其他方式啟用，則 COM 用戶端仍然可以使用它。</span><span class="sxs-lookup"><span data-stu-id="1d67b-125">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="1d67b-126">類型不能是抽象的。</span><span class="sxs-lookup"><span data-stu-id="1d67b-126">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="1d67b-127">COM 用戶端和 .NET 用戶端都無法建立抽象類型。</span><span class="sxs-lookup"><span data-stu-id="1d67b-127">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="1d67b-128">匯出至 COM 時，會壓平合併 Managed 類型的繼承階層。</span><span class="sxs-lookup"><span data-stu-id="1d67b-128">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="1d67b-129">Managed 與 Unmanaged 環境之間的版本設定不同。</span><span class="sxs-lookup"><span data-stu-id="1d67b-129">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="1d67b-130">向 COM 公開之類型與其他 Managed 類型的版本設定特性不同。</span><span class="sxs-lookup"><span data-stu-id="1d67b-130">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d67b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d67b-131">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="1d67b-132">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="1d67b-132">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="1d67b-133">類別介面簡介</span><span class="sxs-lookup"><span data-stu-id="1d67b-133">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="1d67b-134">套用 Interop 屬性</span><span class="sxs-lookup"><span data-stu-id="1d67b-134">Applying Interop Attributes</span></span>](apply-interop-attributes.md)
- [<span data-ttu-id="1d67b-135">封裝 COM 的 .NET Framework 組件</span><span class="sxs-lookup"><span data-stu-id="1d67b-135">Packaging a .NET Framework Assembly for COM</span></span>](../../framework/interop/packaging-an-assembly-for-com.md)
