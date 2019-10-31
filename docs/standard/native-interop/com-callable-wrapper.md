---
title: COM 可呼叫包裝函式
ms.date: 10/23/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
ms.openlocfilehash: 6f2f4055a95dbcea8d7872b5c5fa3ccede8c2c8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120724"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="fc44f-102">COM 可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="fc44f-102">COM Callable Wrapper</span></span>

<span data-ttu-id="fc44f-103">當 COM 用戶端呼叫 .NET 物件時，Common Language Runtime 會建立 Managed 物件和物件的 COM 可呼叫包裝函式 (CCW)。</span><span class="sxs-lookup"><span data-stu-id="fc44f-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="fc44f-104">無法直接參考 .NET 物件，因此 COM 用戶端使用 CCW 做為 Managed 物件的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="fc44f-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="fc44f-105">執行階段會為 Managed 物件建立剛好一個 CCW，不論要求其服務的 COM 用戶端數目有多少。</span><span class="sxs-lookup"><span data-stu-id="fc44f-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="fc44f-106">如下圖所示，多個 COM 用戶端可以保留對公開 INew 介面之 CCW 的參考。</span><span class="sxs-lookup"><span data-stu-id="fc44f-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="fc44f-107">CCW 接著會保留對實作介面且已記憶體回收之 Managed 物件的單一參考。</span><span class="sxs-lookup"><span data-stu-id="fc44f-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="fc44f-108">COM 和 .NET 用戶端都可以同時對相同的 Managed 物件提出要求。</span><span class="sxs-lookup"><span data-stu-id="fc44f-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![保留參考公開 INew 之 CCW 的多個 COM 用戶端。](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="fc44f-110">在 .NET 執行階段內執行的其他類別看不到 COM 可呼叫包裝函式。</span><span class="sxs-lookup"><span data-stu-id="fc44f-110">COM callable wrappers are invisible to other classes running within the .NET runtime.</span></span> <span data-ttu-id="fc44f-111">其主要目的是要封送處理 Managed 和 Unmanaged 程式碼之間的呼叫。不過，CCW 也會管理物件識別和它們所包裝之 Managed 物件的物件存留期。</span><span class="sxs-lookup"><span data-stu-id="fc44f-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="fc44f-112">物件識別</span><span class="sxs-lookup"><span data-stu-id="fc44f-112">Object Identity</span></span>

<span data-ttu-id="fc44f-113">執行階段會從其記憶體回收的堆積來配置 .NET 物件的記憶體，這讓執行階段能視需要在記憶體中四處移動物件。</span><span class="sxs-lookup"><span data-stu-id="fc44f-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="fc44f-114">相反地，執行階段會從未回收的堆積配置記憶體給 CCW，讓 COM 用戶端可以直接參考包裝函式。</span><span class="sxs-lookup"><span data-stu-id="fc44f-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="fc44f-115">物件存留期</span><span class="sxs-lookup"><span data-stu-id="fc44f-115">Object Lifetime</span></span>

<span data-ttu-id="fc44f-116">不同於它所包裝的 .NET 用戶端，CCW 是以傳統 COM 方式計算參考。</span><span class="sxs-lookup"><span data-stu-id="fc44f-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="fc44f-117">當 CCW 上的參考計數到達零時，包裝函式便會釋放對 Managed 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="fc44f-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="fc44f-118">沒有剩餘參考的 Managed 物件會在下一個記憶體回收循環期間回收。</span><span class="sxs-lookup"><span data-stu-id="fc44f-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="fc44f-119">模擬 COM 介面</span><span class="sxs-lookup"><span data-stu-id="fc44f-119">Simulating COM interfaces</span></span>

<span data-ttu-id="fc44f-120">CCW 會以與 COM 強制進行介面型互動一致的方式，向 COM 用戶端公開所有公用且 COM 可見的介面、資料類型和傳回值。</span><span class="sxs-lookup"><span data-stu-id="fc44f-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="fc44f-121">對於 COM 用戶端而言，在 .NET 物件上叫用方法與在 COM 物件上叫用方法相同。</span><span class="sxs-lookup"><span data-stu-id="fc44f-121">For a COM client, invoking methods on a .NET object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="fc44f-122">為了建立這種無縫式的方法，CCW 會製造傳統 COM 介面，例如 **IUnknown** 和 **IDispatch**。</span><span class="sxs-lookup"><span data-stu-id="fc44f-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="fc44f-123">如下圖所示，CCW 會維護對其所包裝之 .NET 物件的單一參考。</span><span class="sxs-lookup"><span data-stu-id="fc44f-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="fc44f-124">COM 用戶端和 .NET 物件會透過 Proxy 和 CCW 虛設常式建構彼此互動。</span><span class="sxs-lookup"><span data-stu-id="fc44f-124">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![此圖顯示 CCW 如何製造 COM 介面。](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="fc44f-126">除了公開受控環境中類別明確實作的介面，.NET 執行階段也會代表物件提供下表所列 COM 介面的實作。</span><span class="sxs-lookup"><span data-stu-id="fc44f-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET runtime supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="fc44f-127">.NET 類別可以藉由提供自己的這些介面實作來覆寫預設行為。</span><span class="sxs-lookup"><span data-stu-id="fc44f-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="fc44f-128">不過，執行階段一律會提供 **IUnknown** 和 **IDispatch** 介面的實作。</span><span class="sxs-lookup"><span data-stu-id="fc44f-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="fc44f-129">介面</span><span class="sxs-lookup"><span data-stu-id="fc44f-129">Interface</span></span>|<span data-ttu-id="fc44f-130">描述</span><span class="sxs-lookup"><span data-stu-id="fc44f-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fc44f-131">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="fc44f-131">**IDispatch**</span></span>|<span data-ttu-id="fc44f-132">提供晚期類型繫結的機制。</span><span class="sxs-lookup"><span data-stu-id="fc44f-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="fc44f-133">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="fc44f-133">**IErrorInfo**</span></span>|<span data-ttu-id="fc44f-134">提供錯誤的文字描述、其來源、說明檔、說明內容，以及定義錯誤之介面的 GUID (.NET 類別一律為 **GUID_NULL**)。</span><span class="sxs-lookup"><span data-stu-id="fc44f-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="fc44f-135">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="fc44f-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="fc44f-136">可讓 COM 用戶端存取 Managed 類別所實作的 **ITypeInfo** 介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span> <span data-ttu-id="fc44f-137">針對未從 COM 匯入的型別傳回 `COR_E_NOTSUPPORTED` .NET Core。</span><span class="sxs-lookup"><span data-stu-id="fc44f-137">Returns `COR_E_NOTSUPPORTED` on .NET Core for types not imported from COM.</span></span> |
|<span data-ttu-id="fc44f-138">**ISupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="fc44f-138">**ISupportErrorInfo**</span></span>|<span data-ttu-id="fc44f-139">可讓 COM 用戶端判斷 Managed 物件是否支援 **IErrorInfo** 介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-139">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="fc44f-140">如果是的話，可讓用戶端取得最新例外狀況物件的指標。</span><span class="sxs-lookup"><span data-stu-id="fc44f-140">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="fc44f-141">所有 Managed 類型都支援 **IErrorInfo** 介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-141">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="fc44f-142">**ITypeInfo** (僅限 .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="fc44f-142">**ITypeInfo** (.NET Framework Only)</span></span>|<span data-ttu-id="fc44f-143">提供與 Tlbexp.exe 所產生之類型資訊完全相同之類別的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="fc44f-143">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="fc44f-144">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="fc44f-144">**IUnknown**</span></span>|<span data-ttu-id="fc44f-145">提供 **IUnknown** 介面的標準實作，COM 用戶端用它來管理 CCW 的存留期，並提供類型強制型轉。</span><span class="sxs-lookup"><span data-stu-id="fc44f-145">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="fc44f-146">Managed 類別也可以提供下表所述的 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-146">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="fc44f-147">介面</span><span class="sxs-lookup"><span data-stu-id="fc44f-147">Interface</span></span>|<span data-ttu-id="fc44f-148">描述</span><span class="sxs-lookup"><span data-stu-id="fc44f-148">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fc44f-149">(\_*classname*) 類別介面</span><span class="sxs-lookup"><span data-stu-id="fc44f-149">The (\_*classname*) class interface</span></span>|<span data-ttu-id="fc44f-150">由執行階段公開且未明確定義的介面，它會公開所有公用介面、方法、屬性和 Managed 物件上明確公開的欄位。</span><span class="sxs-lookup"><span data-stu-id="fc44f-150">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="fc44f-151">**IConnectionPoint** 和 **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="fc44f-151">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="fc44f-152">來源為以委派為基礎之事件的物件介面 (註冊事件訂閱者用的介面)。</span><span class="sxs-lookup"><span data-stu-id="fc44f-152">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="fc44f-153">**IDispatchEx** (僅限 .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="fc44f-153">**IDispatchEx** (.NET Framework Only)</span></span>|<span data-ttu-id="fc44f-154">如果類別實作 **IExpando**，則為執行階段提供的介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-154">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="fc44f-155">**IDispatchEx** 介面是 **IDispatch** 介面的延伸模組，它不同於 **IDispatch**，可進行成員的列舉、新增、刪除和區分大小寫的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fc44f-155">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="fc44f-156">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="fc44f-156">**IEnumVARIANT**</span></span>|<span data-ttu-id="fc44f-157">集合類型類別的介面，如果類別實作 **IEnumerable**，它會列舉集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="fc44f-157">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="fc44f-158">類別介面簡介</span><span class="sxs-lookup"><span data-stu-id="fc44f-158">Introducing the class interface</span></span>

<span data-ttu-id="fc44f-159">類別介面未在 Managed 程式碼中明確定義，它是公開所有公用方法、屬性、欄位和 .NET 物件上明確公開之事件的介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-159">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="fc44f-160">這個介面可以是雙重介面或僅分派介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-160">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="fc44f-161">類別介面會接收 .NET 類別的名稱本身，前面加上底線。</span><span class="sxs-lookup"><span data-stu-id="fc44f-161">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="fc44f-162">例如，對於類別 Mammal，類別介面是 \_Mammal。</span><span class="sxs-lookup"><span data-stu-id="fc44f-162">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="fc44f-163">對於衍生類別，類別介面也會公開和基底類別的所有公用方法、屬性欄位。</span><span class="sxs-lookup"><span data-stu-id="fc44f-163">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="fc44f-164">衍生類別也會為每個基底類別公開類別介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-164">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="fc44f-165">例如，如果類別 Mammal 會延伸類別 MammalSuperclass，而 MammalSuperclass 本身會延伸 System.Object，則 .NET 物件會向 COM 用戶端公開三個類別介面，名稱分別為 \_Mammal、\_MammalSuperclass 及 \_Object。</span><span class="sxs-lookup"><span data-stu-id="fc44f-165">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="fc44f-166">例如，請參考下列 .NET 類別：</span><span class="sxs-lookup"><span data-stu-id="fc44f-166">For example, consider the following .NET class:</span></span>

```vb
' Applies the ClassInterfaceAttribute to set the interface to dual.
<ClassInterface(ClassInterfaceType.AutoDual)> _
' Implicitly extends System.Object.
Public Class Mammal
    Sub Eat()
    Sub Breathe()
    Sub Sleep()
End Class
```

```csharp
// Applies the ClassInterfaceAttribute to set the interface to dual.
[ClassInterface(ClassInterfaceType.AutoDual)]
// Implicitly extends System.Object.
public class Mammal
{
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

<span data-ttu-id="fc44f-167">COM 用戶端可以取得 `_Mammal` 類別介面的指標。</span><span class="sxs-lookup"><span data-stu-id="fc44f-167">The COM client can obtain a pointer to a class interface named `_Mammal`.</span></span> <span data-ttu-id="fc44f-168">在 .NET Framework 上，您可以使用[型別程式庫匯出工具 (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) 工具來產生包含 `_Mammal` 介面定義的型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="fc44f-168">On .NET Framework, you can use the [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) tool to generate a type library containing the `_Mammal` interface definition.</span></span> <span data-ttu-id="fc44f-169">.NET Core 不支援型別程式庫匯出工具。</span><span class="sxs-lookup"><span data-stu-id="fc44f-169">The Type Library Exporter is not supported on .NET Core.</span></span> <span data-ttu-id="fc44f-170">如果 `Mammal` 類別實作一個或多個介面，介面會出現在 coclass 底下。</span><span class="sxs-lookup"><span data-stu-id="fc44f-170">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

```console
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]
interface _Mammal : IDispatch
{
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*
        pRetVal);
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]
        VARIANT_BOOL* pRetVal);
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);
    [id(0x6002000d)] HRESULT Eat();
    [id(0x6002000e)] HRESULT Breathe();
    [id(0x6002000f)] HRESULT Sleep();
}
[uuid(…)]
coclass Mammal
{
    [default] interface _Mammal;
}
```

<span data-ttu-id="fc44f-171">產生類別介面是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="fc44f-171">Generating the class interface is optional.</span></span> <span data-ttu-id="fc44f-172">根據預設，COM Interop 會為您匯出至類型程式庫的每個類別產生一個僅分派介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-172">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="fc44f-173">您可以藉由套用 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 到您的類別，避免或修改自動建立此介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-173">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="fc44f-174">雖然類別介面可以簡化公開 Managed 類別給 COM 的工作，其用法會受到限制。</span><span class="sxs-lookup"><span data-stu-id="fc44f-174">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="fc44f-175">使用類別介面，而不是自行明確定義的話，可能會使 Managed 類別的未來版本控制變複雜。</span><span class="sxs-lookup"><span data-stu-id="fc44f-175">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="fc44f-176">請先閱讀下列方針，再使用類別介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-176">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="fc44f-177">定義明確的介面以供 COM 用戶端使用，而不要產生類別介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-177">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="fc44f-178">由於 COM Interop 會自動產生類別介面，對您類別的後續版本變更可以修改 Common Language Runtime 所公開的類別介面配置。</span><span class="sxs-lookup"><span data-stu-id="fc44f-178">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="fc44f-179">由於 COM 用戶端通常並未預期要處理介面配置中的變更，如果您變更類別的成員配置，它們會中斷。</span><span class="sxs-lookup"><span data-stu-id="fc44f-179">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="fc44f-180">此方針強調公開給 COM 用戶端的介面必須維持不變這樣的概念。</span><span class="sxs-lookup"><span data-stu-id="fc44f-180">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="fc44f-181">若要減少因為不小心重新排列介面配置而中斷 COM 用戶端的風險，請藉由明確定義介面，將對類別的所有變更與介面配置相隔離。</span><span class="sxs-lookup"><span data-stu-id="fc44f-181">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="fc44f-182">使用 **ClassInterfaceAttribute** 解除類別介面的自動產生，並實作類別的明確介面，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="fc44f-182">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

<span data-ttu-id="fc44f-183">**ClassInterfaceType.None** 值可防止在類別中繼資料匯出至型別程式庫時產生類別介面。</span><span class="sxs-lookup"><span data-stu-id="fc44f-183">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="fc44f-184">在上述範例中，COM 用戶端只能透過 `IExplicit` 介面存取 `LoanApp` 類別。</span><span class="sxs-lookup"><span data-stu-id="fc44f-184">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="fc44f-185">避免快取分派識別碼 (DispId)</span><span class="sxs-lookup"><span data-stu-id="fc44f-185">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="fc44f-186">使用類別介面對於指令碼式用戶端、Microsoft Visual Basic 6.0 用戶端，或不會快取介面成員 DispId 的任何晚期繫結用戶端而言，是可接受的選項。</span><span class="sxs-lookup"><span data-stu-id="fc44f-186">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="fc44f-187">DispId 可識別介面成員以啟用晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="fc44f-187">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="fc44f-188">對於類別介面，DispId 的產生是根據成員在介面中的位置。</span><span class="sxs-lookup"><span data-stu-id="fc44f-188">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="fc44f-189">如果您變更成員的順序，並將類別匯出至類型程式庫，您會修改在類別介面中產生的 DispId。</span><span class="sxs-lookup"><span data-stu-id="fc44f-189">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="fc44f-190">若要避免在使用類別介面時中斷晚期繫結 COM 用戶端，請套用具有 **ClassInterfaceType.AutoDispatch** 值的 **ClassInterfaceAttribute**。</span><span class="sxs-lookup"><span data-stu-id="fc44f-190">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="fc44f-191">這個值會實作僅分派類別介面，但會略過來自類型程式庫的介面描述。</span><span class="sxs-lookup"><span data-stu-id="fc44f-191">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="fc44f-192">沒有介面描述，用戶端將無法在編譯時間快取 DispId。</span><span class="sxs-lookup"><span data-stu-id="fc44f-192">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="fc44f-193">雖然這是類別介面的預設介面類型，您仍可以明確地套用屬性值。</span><span class="sxs-lookup"><span data-stu-id="fc44f-193">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

<span data-ttu-id="fc44f-194">若要在執行階段取得介面成員的 DispId，COM 用戶端可以呼叫 **IDispatch.GetIdsOfNames**。</span><span class="sxs-lookup"><span data-stu-id="fc44f-194">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="fc44f-195">若要在介面上叫用方法，請將傳回的 DispId 作為引數傳遞給 **IDispatch.Invoke**。</span><span class="sxs-lookup"><span data-stu-id="fc44f-195">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="fc44f-196">限制針對類別介面使用雙重介面選項。</span><span class="sxs-lookup"><span data-stu-id="fc44f-196">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="fc44f-197">雙重介面可讓 COM 用戶端進行介面成員的早期和晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="fc44f-197">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="fc44f-198">在設計階段和測試期間，您可能會發現將類別介面設為雙重很有用。</span><span class="sxs-lookup"><span data-stu-id="fc44f-198">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="fc44f-199">對於絕對不會修改的 Managed 類別 (和其基底類別)，此選項也是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="fc44f-199">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="fc44f-200">在其他情況下，請避免將類別介面設定為雙重。</span><span class="sxs-lookup"><span data-stu-id="fc44f-200">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="fc44f-201">自動產生的雙重介面可能適合於少數情況，不過，通常它會造成與版本相關的複雜性。</span><span class="sxs-lookup"><span data-stu-id="fc44f-201">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="fc44f-202">例如，使用衍生類別之類別介面的 COM 用戶端，可能會因為對基底類別的變更而輕易地中斷。</span><span class="sxs-lookup"><span data-stu-id="fc44f-202">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="fc44f-203">當協力廠商提供基底類別時，類別介面的配置會超出您的控制。</span><span class="sxs-lookup"><span data-stu-id="fc44f-203">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="fc44f-204">此外，不同於僅分派介面，雙重介面 (**ClassInterfaceType.AutoDual**) 會在匯出的型別程式庫中提供類別介面的描述。</span><span class="sxs-lookup"><span data-stu-id="fc44f-204">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="fc44f-205">此類描述鼓勵晚期繫結的用戶端在編譯時間快取 DispId。</span><span class="sxs-lookup"><span data-stu-id="fc44f-205">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="fc44f-206">請確定所有 COM 事件通知都是晚期繫結的。</span><span class="sxs-lookup"><span data-stu-id="fc44f-206">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="fc44f-207">根據預設，COM 型別資訊會直接內嵌到受控組件，而不需主要的 interop 組件 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="fc44f-207">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="fc44f-208">不過，內嵌類型資訊的其中一個限制是它不支援透過早期繫結 vtable 呼叫的 COM 事件通知傳遞，而僅支援晚期繫結的 `IDispatch::Invoke` 呼叫。</span><span class="sxs-lookup"><span data-stu-id="fc44f-208">However, one of the limitations of embedded type information is that it does not support delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="fc44f-209">如果您的應用程式需要對 COM 事件介面方法進行早期繫結呼叫，您可以在 Visual Studio 中將**內嵌 Interop 型別**屬性設定為 `true`，或在您的專案檔中包含下列元素：</span><span class="sxs-lookup"><span data-stu-id="fc44f-209">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="fc44f-210">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc44f-210">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="fc44f-211">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="fc44f-211">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="fc44f-212">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="fc44f-212">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="fc44f-213">將 .NET 核心元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="fc44f-213">Exposing .NET Core Components to COM</span></span>](../../core/native-interop/expose-components-to-com.md)
- [<span data-ttu-id="fc44f-214">限定互通的 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="fc44f-214">Qualifying .NET Types for Interoperation</span></span>](qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="fc44f-215">執行階段可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="fc44f-215">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
