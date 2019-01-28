---
title: 限定互通的 .NET 類型
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a40b9524990213eaaf2ed78503b6f831776306ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524308"
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="fa4ef-102">限定互通的 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="fa4ef-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="fa4ef-103">如果您想要向 COM 應用程式公開組件中的類型，請考慮設計階段的 COM Interop 需求。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="fa4ef-104">當您遵守下列方針時，Managed 類型 (類別、介面、結構和列舉) 會與 COM 類型緊密整合：</span><span class="sxs-lookup"><span data-stu-id="fa4ef-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
-   <span data-ttu-id="fa4ef-105">類別應該明確地實作介面。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="fa4ef-106">雖然 COM Interop 提供機制來自動產生包含類別之所有成員和其基底類別成員的介面，最好是目前提供明確的介面。但是最好是提供明確介面。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="fa4ef-107">自動產生的介面稱為類別介面。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="fa4ef-108">如需方針，請參閱[類別介面簡介](com-callable-wrapper.md#introducing-the-class-interface)。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="fa4ef-109">您可以使用 Visual Basic、C# 和 C++ 在程式碼中併入介面定義，而不需使用介面定義語言 (IDL) 或其對等項目。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="fa4ef-110">如需語法詳細資訊，請參閱您的語言文件。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-110">For syntax details, see your language documentation.</span></span>  
  
-   <span data-ttu-id="fa4ef-111">Managed 類型必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="fa4ef-112">只有組件中的公用類型才會註冊並匯出至型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="fa4ef-113">因此，只有 COM 才能看到公用類型。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="fa4ef-114">Managed 類型會向可能未向 COM 公開的其他 Managed 程式碼公開功能。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="fa4ef-115">例如，不會向 COM 用戶端公開參數化建構函式、靜態方法和常數欄位。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="fa4ef-116">此外，執行階段將資料封送處理至類型或從中封送處理資料時，可能會複製或轉換資料。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
-   <span data-ttu-id="fa4ef-117">方法、屬性、欄位和事件必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="fa4ef-118">如果要讓 COM 看到公用類型的成員，則它們也必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="fa4ef-119">您可以套用 <xref:System.Runtime.InteropServices.ComVisibleAttribute>，以限制組件、公用類型或公用類型的公用成員的可見性。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="fa4ef-120">根據預設，會顯示所有公用類型和成員。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-120">By default, all public types and members are visible.</span></span>  
  
-   <span data-ttu-id="fa4ef-121">類型必須具有要從 COM 啟用的公用預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="fa4ef-122">COM 可以看到 Managed 公用類型。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="fa4ef-123">不過，沒有公用預設建構函式 (沒有引數的建構函式)，COM 用戶端就無法建立該類型。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="fa4ef-124">如果該類型是透過一些其他方式啟用，則 COM 用戶端仍然可以使用它。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
-   <span data-ttu-id="fa4ef-125">類型不能是抽象的。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="fa4ef-126">COM 用戶端和 .NET 用戶端都無法建立抽象類型。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="fa4ef-127">匯出至 COM 時，會壓平合併 Managed 類型的繼承階層。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="fa4ef-128">Managed 與 Unmanaged 環境之間的版本設定不同。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="fa4ef-129">向 COM 公開之類型與其他 Managed 類型的版本設定特性不同。</span><span class="sxs-lookup"><span data-stu-id="fa4ef-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4ef-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa4ef-130">See also</span></span>
- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="fa4ef-131">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="fa4ef-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="fa4ef-132">類別介面簡介</span><span class="sxs-lookup"><span data-stu-id="fa4ef-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="fa4ef-133">套用 Interop 屬性</span><span class="sxs-lookup"><span data-stu-id="fa4ef-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)
- [<span data-ttu-id="fa4ef-134">封裝 COM 的組件</span><span class="sxs-lookup"><span data-stu-id="fa4ef-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
