---
title: "物件的預設封送處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c5bfafcad5f1f60e7e763b69f220188517d29f17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="46d1b-102">物件的預設封送處理</span><span class="sxs-lookup"><span data-stu-id="46d1b-102">Default Marshaling for Objects</span></span>
<span data-ttu-id="46d1b-103">類型為 <xref:System.Object?displayProperty=nameWithType> 的參數和欄位可以向 Unmanaged 程式碼公開為下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="46d1b-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>  
  
-   <span data-ttu-id="46d1b-104">Variant，當物件是參數時。</span><span class="sxs-lookup"><span data-stu-id="46d1b-104">A variant when the object is a parameter.</span></span>  
  
-   <span data-ttu-id="46d1b-105">介面，當物件是結構欄位時。</span><span class="sxs-lookup"><span data-stu-id="46d1b-105">An interface when the object is a structure field.</span></span>  
  
 <span data-ttu-id="46d1b-106">只有 COM Interop 支援封送處理物件類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="46d1b-107">預設行為是封送處理 COM Variant 的物件。</span><span class="sxs-lookup"><span data-stu-id="46d1b-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="46d1b-108">這些規則只適用於**物件**類型，不適用於衍生自**物件**類別的強型別物件。</span><span class="sxs-lookup"><span data-stu-id="46d1b-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>  
  
 <span data-ttu-id="46d1b-109">本主題提供下列有關封送處理物件類型的額外資訊：</span><span class="sxs-lookup"><span data-stu-id="46d1b-109">This topic provides the following additional information about marshaling object types:</span></span>  
  
-   [<span data-ttu-id="46d1b-110">封送處理選項</span><span class="sxs-lookup"><span data-stu-id="46d1b-110">Marshaling Options</span></span>](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [<span data-ttu-id="46d1b-111">將物件封送處理成介面</span><span class="sxs-lookup"><span data-stu-id="46d1b-111">Marshaling Object to Interface</span></span>](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [<span data-ttu-id="46d1b-112">將物件封送處理成 Variant</span><span class="sxs-lookup"><span data-stu-id="46d1b-112">Marshaling Object to Variant</span></span>](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [<span data-ttu-id="46d1b-113">將 Variant 封送處理成物件</span><span class="sxs-lookup"><span data-stu-id="46d1b-113">Marshaling Variant to Object</span></span>](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [<span data-ttu-id="46d1b-114">封送處理的 ByRef Variant</span><span class="sxs-lookup"><span data-stu-id="46d1b-114">Marshaling ByRef Variants</span></span>](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a><span data-ttu-id="46d1b-115">封送處理選項</span><span class="sxs-lookup"><span data-stu-id="46d1b-115">Marshaling Options</span></span>  
 <span data-ttu-id="46d1b-116">下表顯示**物件**資料類型的封送處理選項。</span><span class="sxs-lookup"><span data-stu-id="46d1b-116">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="46d1b-117"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理物件。</span><span class="sxs-lookup"><span data-stu-id="46d1b-117">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>  
  
|<span data-ttu-id="46d1b-118">列舉類型</span><span class="sxs-lookup"><span data-stu-id="46d1b-118">Enumeration type</span></span>|<span data-ttu-id="46d1b-119">Unmanaged 格式的描述</span><span class="sxs-lookup"><span data-stu-id="46d1b-119">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="46d1b-120">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="46d1b-120">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="46d1b-121">(參數預設值)</span><span class="sxs-lookup"><span data-stu-id="46d1b-121">(default for parameters)</span></span>|<span data-ttu-id="46d1b-122">COM 樣式的 Variant。</span><span class="sxs-lookup"><span data-stu-id="46d1b-122">A COM-style variant.</span></span>|  
|<span data-ttu-id="46d1b-123">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="46d1b-123">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="46d1b-124">如果可能的話，為 **IDispatch** 介面；否則為 **IUnknown** 介面。</span><span class="sxs-lookup"><span data-stu-id="46d1b-124">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|  
|<span data-ttu-id="46d1b-125">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="46d1b-125">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="46d1b-126">(欄位預設值)</span><span class="sxs-lookup"><span data-stu-id="46d1b-126">(default for fields)</span></span>|<span data-ttu-id="46d1b-127">**IUnknown** 介面。</span><span class="sxs-lookup"><span data-stu-id="46d1b-127">An **IUnknown** interface.</span></span>|  
|<span data-ttu-id="46d1b-128">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="46d1b-128">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="46d1b-129">**IDispatch** 介面。</span><span class="sxs-lookup"><span data-stu-id="46d1b-129">An **IDispatch** interface.</span></span>|  
  
 <span data-ttu-id="46d1b-130">下例顯示 `MarshalObject` 的 Managed 介面定義。</span><span class="sxs-lookup"><span data-stu-id="46d1b-130">The following example shows the managed interface definition for `MarshalObject`.</span></span>  
  
```vb  
Interface MarshalObject  
   Sub SetVariant(o As Object)  
   Sub SetVariantRef(ByRef o As Object)  
   Function GetVariant() As Object  
  
   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)  
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _  
      As Object)  
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object  
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)  
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _  
      As Object)  
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object  
End Interface  
```  
  
```csharp  
interface MarshalObject {  
   void SetVariant(Object o);  
   void SetVariantRef(ref Object o);  
   Object GetVariant();  
  
   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);  
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);  
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();  
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);  
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);  
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();  
}  
```  
  
 <span data-ttu-id="46d1b-131">下列程式碼會將 `MarshalObject` 介面匯出至型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="46d1b-131">The following code exports the `MarshalObject` interface to a type library.</span></span>  
  
```  
interface MarshalObject {  
   HRESULT SetVariant([in] VARIANT o);  
   HRESULT SetVariantRef([in,out] VARIANT *o);  
   HRESULT GetVariant([out,retval] VARIANT *o)   
   HRESULT SetIDispatch([in] IDispatch *o);  
   HRESULT SetIDispatchRef([in,out] IDispatch **o);  
   HRESULT GetIDispatch([out,retval] IDispatch **o)   
   HRESULT SetIUnknown([in] IUnknown *o);  
   HRESULT SetIUnknownRef([in,out] IUnknown **o);  
   HRESULT GetIUnknown([out,retval] IUnknown **o)   
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="46d1b-132">Interop 封送處理器會呼叫之後，自動釋放 Variant 內所有的配置物件。</span><span class="sxs-lookup"><span data-stu-id="46d1b-132">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>  
  
 <span data-ttu-id="46d1b-133">下例會顯示格式化的實值型別。</span><span class="sxs-lookup"><span data-stu-id="46d1b-133">The following example shows a formatted value type.</span></span>  
  
```vb  
Public Structure ObjectHolder  
   Dim o1 As Object  
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object  
End Structure  
```  
  
```csharp  
public struct ObjectHolder {  
   Object o1;  
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;  
}  
```  
  
 <span data-ttu-id="46d1b-134">下列程式碼會將格式化的類型匯出至型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="46d1b-134">The following code exports the formatted type to a type library.</span></span>  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a><span data-ttu-id="46d1b-135">將物件封送處理成介面</span><span class="sxs-lookup"><span data-stu-id="46d1b-135">Marshaling Object to Interface</span></span>  
 <span data-ttu-id="46d1b-136">向 COM 將物件公開為介面時，該介面是 Managed 類型 <xref:System.Object> 的類別介面 (**_Object** 介面)。</span><span class="sxs-lookup"><span data-stu-id="46d1b-136">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="46d1b-137">在產生的型別程式庫中，這個介面類型為 **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) 或 **IUnknown** (**UnmanagedType.IUnknown**)。</span><span class="sxs-lookup"><span data-stu-id="46d1b-137">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="46d1b-138">COM 用戶端可以動態方式叫用 Managed 類別的成員，或其衍生類別透過 **_Object** 介面所實作的任何成員。</span><span class="sxs-lookup"><span data-stu-id="46d1b-138">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="46d1b-139">用戶端也可以呼叫 **QueryInterface** 取得 Managed 類型明確實作的任何其他介面。</span><span class="sxs-lookup"><span data-stu-id="46d1b-139">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a><span data-ttu-id="46d1b-140">將物件封送處理成 Variant</span><span class="sxs-lookup"><span data-stu-id="46d1b-140">Marshaling Object to Variant</span></span>  
 <span data-ttu-id="46d1b-141">當物件封送處理成 Variant 時，會根據下列規則在執行階段決定內部的 Variant 類型：</span><span class="sxs-lookup"><span data-stu-id="46d1b-141">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>  
  
-   <span data-ttu-id="46d1b-142">如果物件參考為 null (Visual Basic 為**Nothing**)，物件會封送處理成 **VT_EMPTY** 類型的 Variant。</span><span class="sxs-lookup"><span data-stu-id="46d1b-142">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>  
  
-   <span data-ttu-id="46d1b-143">如果物件是下表所列任一類型的執行個體，則產生的 Variant 類型是由封送處理器內建的規則決定，並顯示在資料表中。</span><span class="sxs-lookup"><span data-stu-id="46d1b-143">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>  
  
-   <span data-ttu-id="46d1b-144">需要明確控制封送處理行為的其他物件，可以實作 <xref:System.IConvertible> 介面。</span><span class="sxs-lookup"><span data-stu-id="46d1b-144">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="46d1b-145">在此情況下，Variant 類型是由 <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> 方法傳回的類型程式碼所決定。</span><span class="sxs-lookup"><span data-stu-id="46d1b-145">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="46d1b-146">否則，物件會封送處理成 **VT_UNKNOWN** 類型的 Variant。</span><span class="sxs-lookup"><span data-stu-id="46d1b-146">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>  
  
### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="46d1b-147">將系統類型封送處理為 Variant</span><span class="sxs-lookup"><span data-stu-id="46d1b-147">Marshaling System Types to Variant</span></span>  
 <span data-ttu-id="46d1b-148">下表顯示 Managed 物件類型及其對應的 COM Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-148">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="46d1b-149">只有當正在呼叫的方法簽章是 <xref:System.Object?displayProperty=nameWithType> 類型時，這些類型才會轉換。</span><span class="sxs-lookup"><span data-stu-id="46d1b-149">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
|<span data-ttu-id="46d1b-150">物件類型</span><span class="sxs-lookup"><span data-stu-id="46d1b-150">Object type</span></span>|<span data-ttu-id="46d1b-151">COM Variant 類型</span><span class="sxs-lookup"><span data-stu-id="46d1b-151">COM variant type</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="46d1b-152">Null 物件參考 (在 Visual Basic 中為 **Nothing**)。</span><span class="sxs-lookup"><span data-stu-id="46d1b-152">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="46d1b-153">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="46d1b-153">**VT_EMPTY**</span></span>|  
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="46d1b-154">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="46d1b-154">**VT_NULL**</span></span>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="46d1b-155">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="46d1b-155">**VT_ERROR**</span></span>|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="46d1b-156">**VT_ERROR** 與 **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="46d1b-156">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="46d1b-157">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="46d1b-157">**VT_DISPATCH**</span></span>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="46d1b-158">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="46d1b-158">**VT_UNKNOWN**</span></span>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="46d1b-159">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="46d1b-159">**VT_CY**</span></span>|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="46d1b-160">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="46d1b-160">**VT_BOOL**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="46d1b-161">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="46d1b-161">**VT_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="46d1b-162">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="46d1b-162">**VT_UI1**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="46d1b-163">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="46d1b-163">**VT_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="46d1b-164">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="46d1b-164">**VT_UI2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="46d1b-165">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="46d1b-165">**VT_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="46d1b-166">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="46d1b-166">**VT_UI4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="46d1b-167">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="46d1b-167">**VT_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="46d1b-168">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="46d1b-168">**VT_UI8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="46d1b-169">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="46d1b-169">**VT_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="46d1b-170">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="46d1b-170">**VT_R8**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="46d1b-171">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="46d1b-171">**VT_DECIMAL**</span></span>|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="46d1b-172">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="46d1b-172">**VT_DATE**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="46d1b-173">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="46d1b-173">**VT_BSTR**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="46d1b-174">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="46d1b-174">**VT_INT**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="46d1b-175">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="46d1b-175">**VT_UINT**</span></span>|  
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="46d1b-176">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="46d1b-176">**VT_ARRAY**</span></span>|  
  
 <span data-ttu-id="46d1b-177">使用前一個範例中定義的 `MarshalObject` 介面，下列程式碼範例示範如何將各種類型的 Variant 傳送到 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="46d1b-177">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>  
  
```vb  
Dim mo As New MarshalObject()  
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.  
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.  
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.  
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.  
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.  
```  
  
```csharp  
MarshalObject mo = new MarshalObject();  
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.  
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.  
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.  
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.  
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.  
```  
  
 <span data-ttu-id="46d1b-178">沒有對應 Managed 類型的 COM 類型，可以使用 <xref:System.Runtime.InteropServices.ErrorWrapper>、<xref:System.Runtime.InteropServices.DispatchWrapper>、<xref:System.Runtime.InteropServices.UnknownWrapper> 和 <xref:System.Runtime.InteropServices.CurrencyWrapper> 等包裝函式類別予以封送處理。</span><span class="sxs-lookup"><span data-stu-id="46d1b-178">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="46d1b-179">下列程式碼範例示範如何使用這些包裝函式將各種類型的 Variant 傳送到 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="46d1b-179">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
' Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(New UnknownWrapper(inew))  
' Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(New DispatchWrapper(inew))  
' Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(New ErrorWrapper(&H80054002))  
' Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))  
```  
  
```csharp  
using System.Runtime.InteropServices;  
// Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(new UnknownWrapper(inew));  
// Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(new DispatchWrapper(inew));  
// Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(new ErrorWrapper(0x80054002));  
// Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));  
```  
  
 <span data-ttu-id="46d1b-180">包裝函式類別是在 <xref:System.Runtime.InteropServices> 命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="46d1b-180">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="46d1b-181">將 IConvertible 介面封送處理為 Variant</span><span class="sxs-lookup"><span data-stu-id="46d1b-181">Marshaling the IConvertible Interface to Variant</span></span>  
 <span data-ttu-id="46d1b-182">上節中未列出的其他類型，可以透過實作 <xref:System.IConvertible> 介面來控制封送處理的方式。</span><span class="sxs-lookup"><span data-stu-id="46d1b-182">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="46d1b-183">如果物件實作 **IConvertible** 介面，從 <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> 方法傳回的 <xref:System.TypeCode> 列舉值會在執行階段決定 COM Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-183">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="46d1b-184">下表顯示可能的 **TypeCode** 列舉值和每個值對應的 COM Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-184">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>  
  
|<span data-ttu-id="46d1b-185">TypeCode</span><span class="sxs-lookup"><span data-stu-id="46d1b-185">TypeCode</span></span>|<span data-ttu-id="46d1b-186">COM Variant 類型</span><span class="sxs-lookup"><span data-stu-id="46d1b-186">COM variant type</span></span>|  
|--------------|----------------------|  
|<span data-ttu-id="46d1b-187">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="46d1b-187">**TypeCode.Empty**</span></span>|<span data-ttu-id="46d1b-188">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="46d1b-188">**VT_EMPTY**</span></span>|  
|<span data-ttu-id="46d1b-189">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="46d1b-189">**TypeCode.Object**</span></span>|<span data-ttu-id="46d1b-190">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="46d1b-190">**VT_UNKNOWN**</span></span>|  
|<span data-ttu-id="46d1b-191">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="46d1b-191">**TypeCode.DBNull**</span></span>|<span data-ttu-id="46d1b-192">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="46d1b-192">**VT_NULL**</span></span>|  
|<span data-ttu-id="46d1b-193">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="46d1b-193">**TypeCode.Boolean**</span></span>|<span data-ttu-id="46d1b-194">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="46d1b-194">**VT_BOOL**</span></span>|  
|<span data-ttu-id="46d1b-195">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="46d1b-195">**TypeCode.Char**</span></span>|<span data-ttu-id="46d1b-196">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="46d1b-196">**VT_UI2**</span></span>|  
|<span data-ttu-id="46d1b-197">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="46d1b-197">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="46d1b-198">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="46d1b-198">**VT_I1**</span></span>|  
|<span data-ttu-id="46d1b-199">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="46d1b-199">**TypeCode.Byte**</span></span>|<span data-ttu-id="46d1b-200">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="46d1b-200">**VT_UI1**</span></span>|  
|<span data-ttu-id="46d1b-201">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="46d1b-201">**TypeCode.Int16**</span></span>|<span data-ttu-id="46d1b-202">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="46d1b-202">**VT_I2**</span></span>|  
|<span data-ttu-id="46d1b-203">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="46d1b-203">**TypeCode.UInt16**</span></span>|<span data-ttu-id="46d1b-204">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="46d1b-204">**VT_UI2**</span></span>|  
|<span data-ttu-id="46d1b-205">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="46d1b-205">**TypeCode.Int32**</span></span>|<span data-ttu-id="46d1b-206">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="46d1b-206">**VT_I4**</span></span>|  
|<span data-ttu-id="46d1b-207">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="46d1b-207">**TypeCode.UInt32**</span></span>|<span data-ttu-id="46d1b-208">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="46d1b-208">**VT_UI4**</span></span>|  
|<span data-ttu-id="46d1b-209">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="46d1b-209">**TypeCode.Int64**</span></span>|<span data-ttu-id="46d1b-210">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="46d1b-210">**VT_I8**</span></span>|  
|<span data-ttu-id="46d1b-211">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="46d1b-211">**TypeCode.UInt64**</span></span>|<span data-ttu-id="46d1b-212">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="46d1b-212">**VT_UI8**</span></span>|  
|<span data-ttu-id="46d1b-213">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="46d1b-213">**TypeCode.Single**</span></span>|<span data-ttu-id="46d1b-214">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="46d1b-214">**VT_R4**</span></span>|  
|<span data-ttu-id="46d1b-215">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="46d1b-215">**TypeCode.Double**</span></span>|<span data-ttu-id="46d1b-216">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="46d1b-216">**VT_R8**</span></span>|  
|<span data-ttu-id="46d1b-217">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="46d1b-217">**TypeCode.Decimal**</span></span>|<span data-ttu-id="46d1b-218">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="46d1b-218">**VT_DECIMAL**</span></span>|  
|<span data-ttu-id="46d1b-219">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="46d1b-219">**TypeCode.DateTime**</span></span>|<span data-ttu-id="46d1b-220">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="46d1b-220">**VT_DATE**</span></span>|  
|<span data-ttu-id="46d1b-221">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="46d1b-221">**TypeCode.String**</span></span>|<span data-ttu-id="46d1b-222">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="46d1b-222">**VT_BSTR**</span></span>|  
|<span data-ttu-id="46d1b-223">不支援。</span><span class="sxs-lookup"><span data-stu-id="46d1b-223">Not supported.</span></span>|<span data-ttu-id="46d1b-224">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="46d1b-224">**VT_INT**</span></span>|  
|<span data-ttu-id="46d1b-225">不支援。</span><span class="sxs-lookup"><span data-stu-id="46d1b-225">Not supported.</span></span>|<span data-ttu-id="46d1b-226">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="46d1b-226">**VT_UINT**</span></span>|  
|<span data-ttu-id="46d1b-227">不支援。</span><span class="sxs-lookup"><span data-stu-id="46d1b-227">Not supported.</span></span>|<span data-ttu-id="46d1b-228">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="46d1b-228">**VT_ARRAY**</span></span>|  
|<span data-ttu-id="46d1b-229">不支援。</span><span class="sxs-lookup"><span data-stu-id="46d1b-229">Not supported.</span></span>|<span data-ttu-id="46d1b-230">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="46d1b-230">**VT_RECORD**</span></span>|  
|<span data-ttu-id="46d1b-231">不支援。</span><span class="sxs-lookup"><span data-stu-id="46d1b-231">Not supported.</span></span>|<span data-ttu-id="46d1b-232">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="46d1b-232">**VT_CY**</span></span>|  
|<span data-ttu-id="46d1b-233">不支援。</span><span class="sxs-lookup"><span data-stu-id="46d1b-233">Not supported.</span></span>|<span data-ttu-id="46d1b-234">**VT_Variant**</span><span class="sxs-lookup"><span data-stu-id="46d1b-234">**VT_VARIANT**</span></span>|  
  
 <span data-ttu-id="46d1b-235">COM Variant 的值是透過呼叫 **IConvertible.To** *Type* 介面所決定；其中 **To** *Type* 是轉換常式，對應到從 **IConvertible.GetTypeCode** 傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-235">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="46d1b-236">例如，從 **IConvertible.GetTypeCode** 傳回 **TypeCode.Double** 的物件，會封送處理成 **VT_R8** 類型的 COM Variant。</span><span class="sxs-lookup"><span data-stu-id="46d1b-236">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="46d1b-237">您可以透過轉換為 **IConvertible** 介面及呼叫 <xref:System.IConvertible.ToDouble%2A> 方法，取得 Variant 的值 (儲存在 COM Variant 的 **dblVal** 欄位)。</span><span class="sxs-lookup"><span data-stu-id="46d1b-237">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a><span data-ttu-id="46d1b-238">將 Variant 封送處理成物件</span><span class="sxs-lookup"><span data-stu-id="46d1b-238">Marshaling Variant to Object</span></span>  
 <span data-ttu-id="46d1b-239">將 Variant 封送處理成物件時，已封送處理的 Variant 類型 (有時是值)，可以判斷所產生的物件類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-239">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="46d1b-240">下表可以識別當 Variant 從 COM 傳遞至 .NET ＦFramework 時，封送處理器建立的每個 Variant 類型和對應的物件類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-240">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>  
  
|<span data-ttu-id="46d1b-241">COM Variant 類型</span><span class="sxs-lookup"><span data-stu-id="46d1b-241">COM variant type</span></span>|<span data-ttu-id="46d1b-242">物件類型</span><span class="sxs-lookup"><span data-stu-id="46d1b-242">Object type</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="46d1b-243">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="46d1b-243">**VT_EMPTY**</span></span>|<span data-ttu-id="46d1b-244">Null 物件參考 (在 Visual Basic 中為 **Nothing**)。</span><span class="sxs-lookup"><span data-stu-id="46d1b-244">Null object reference (**Nothing** in Visual Basic).</span></span>|  
|<span data-ttu-id="46d1b-245">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="46d1b-245">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-246">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="46d1b-246">**VT_DISPATCH**</span></span>|<span data-ttu-id="46d1b-247">**System.__ComObject** or null if (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="46d1b-247">**System.__ComObject** or null if (pdispVal == null)</span></span>|  
|<span data-ttu-id="46d1b-248">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="46d1b-248">**VT_UNKNOWN**</span></span>|<span data-ttu-id="46d1b-249">**System.__ComObject** or null if (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="46d1b-249">**System.__ComObject** or null if (punkVal == null)</span></span>|  
|<span data-ttu-id="46d1b-250">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="46d1b-250">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-251">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="46d1b-251">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-252">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="46d1b-252">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-253">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="46d1b-253">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-254">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="46d1b-254">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-255">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="46d1b-255">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-256">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="46d1b-256">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-257">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="46d1b-257">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-258">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="46d1b-258">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-259">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="46d1b-259">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-260">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="46d1b-260">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-261">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="46d1b-261">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-262">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="46d1b-262">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-263">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="46d1b-263">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-264">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="46d1b-264">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-265">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="46d1b-265">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-266">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="46d1b-266">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-267">**VT_ARRAY** &#124; **VT_\***</span><span class="sxs-lookup"><span data-stu-id="46d1b-267">**VT_ARRAY** &#124; **VT_\***</span></span>|<xref:System.Array?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-268">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="46d1b-268">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="46d1b-269">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="46d1b-269">**VT_RECORD**</span></span>|<span data-ttu-id="46d1b-270">對應 Boxed 實值型別。</span><span class="sxs-lookup"><span data-stu-id="46d1b-270">Corresponding boxed value type.</span></span>|  
|<span data-ttu-id="46d1b-271">**VT_Variant**</span><span class="sxs-lookup"><span data-stu-id="46d1b-271">**VT_VARIANT**</span></span>|<span data-ttu-id="46d1b-272">不支援。</span><span class="sxs-lookup"><span data-stu-id="46d1b-272">Not supported.</span></span>|  
  
 <span data-ttu-id="46d1b-273">從 COM 傳遞至 Managed 程式碼再回到 COM 的 Variant 類型，在呼叫期間可能不會保留相同的 Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-273">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="46d1b-274">當 **VT_DISPATCH** 類型的 Variant 從 COM 傳遞至 .NET Framework 時，請考慮會發生什麼情況。</span><span class="sxs-lookup"><span data-stu-id="46d1b-274">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="46d1b-275">在封送處理期間，Variant 會轉換成 <xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="46d1b-275">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="46d1b-276">如果接著將**物件**傳送回 COM，它會封送處理回 **VT_UNKNOWN** 類型的 Variant。</span><span class="sxs-lookup"><span data-stu-id="46d1b-276">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="46d1b-277">當物件從 Managed 程式碼封送處理到 COM 時產生的 Variant，不保證和最初用來產生物件的 Variant 是同一類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-277">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a><span data-ttu-id="46d1b-278">封送處理 ByRef Variant</span><span class="sxs-lookup"><span data-stu-id="46d1b-278">Marshaling ByRef Variants</span></span>  
 <span data-ttu-id="46d1b-279">雖然 Variant 本身可以傳值方式或傳址方式傳遞，**VT_BYREF** 旗標也可搭配任何 Variant 類型使用來表示 Variant 的內容正在以傳址方式傳遞，不是以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="46d1b-279">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="46d1b-280">以傳址方式封送處理的 Variant 和封送處理設有 **VT_BYREF** 旗標的 Variant 之間的差異，會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="46d1b-280">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="46d1b-281">下圖將釐清這些差異。</span><span class="sxs-lookup"><span data-stu-id="46d1b-281">The following illustration clarifies the differences.</span></span>  
  
 <span data-ttu-id="46d1b-282">![在堆疊上傳遞的 Variant](../../../docs/framework/interop/media/interopvariant.gif "InteropVariant")</span><span class="sxs-lookup"><span data-stu-id="46d1b-282">![Variant passed on the stack](../../../docs/framework/interop/media/interopvariant.gif "interopvariant")</span></span>  
<span data-ttu-id="46d1b-283">以傳值方式傳遞和以傳址方式傳遞的 Variant</span><span class="sxs-lookup"><span data-stu-id="46d1b-283">Variants passed by value and by reference</span></span>  
  
 <span data-ttu-id="46d1b-284">**依值封送處理物件和 Variant 的預設行為**</span><span class="sxs-lookup"><span data-stu-id="46d1b-284">**Default behavior for marshaling objects and variants by value**</span></span>  
  
-   <span data-ttu-id="46d1b-285">當從 Managed 程式碼將物件傳送至 COM 時，會使用[將物件封送處理成 Variant](#cpcondefaultmarshalingforobjectsanchor3) 中定義的規則，將物件的內容複製到封送處理器所建立的新 Variant 中。</span><span class="sxs-lookup"><span data-stu-id="46d1b-285">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#cpcondefaultmarshalingforobjectsanchor3).</span></span> <span data-ttu-id="46d1b-286">對 Unmanaged 端的 Variant 所做的變更，在從呼叫傳回時，不會傳播回原始物件。</span><span class="sxs-lookup"><span data-stu-id="46d1b-286">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>  
  
-   <span data-ttu-id="46d1b-287">當從 COM 將 Variant 傳送至 Managed 程式碼時，會使用[將 Variant 封送處理成物件](#cpcondefaultmarshalingforobjectsanchor4)中定義的規則，將 Variant 的內容複製到新建立的物件中。</span><span class="sxs-lookup"><span data-stu-id="46d1b-287">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#cpcondefaultmarshalingforobjectsanchor4).</span></span> <span data-ttu-id="46d1b-288">對 Unmanaged 端的 Variant 所做的變更，在從呼叫傳回時，不會傳播回原始物件。</span><span class="sxs-lookup"><span data-stu-id="46d1b-288">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>  
  
 <span data-ttu-id="46d1b-289">**依參考封送處理物件和 Variant 的預設行為**</span><span class="sxs-lookup"><span data-stu-id="46d1b-289">**Default behavior for marshaling objects and variants by reference**</span></span>  
  
 <span data-ttu-id="46d1b-290">若要將變更傳播回呼叫端，必須以傳址方式傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="46d1b-290">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="46d1b-291">例如，您可以在 C# 中使用 **ref** 關鍵字 (或在 Visual Basic 的 Managed 程式碼中使用 **ByRef**)，以傳址方式傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="46d1b-291">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="46d1b-292">在 COM 中，參考參數是使用 **Variant \*** 等指標傳遞。</span><span class="sxs-lookup"><span data-stu-id="46d1b-292">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>  
  
-   <span data-ttu-id="46d1b-293">以傳址方式將物件傳遞給 COM 時，封送處理器會建立新的 Variant，先將物件參考的內容複製到 Variant，再進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="46d1b-293">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="46d1b-294">Variant 會傳遞至 Unmanaged 函式，使用者可在此任意變更 Variant 的內容。</span><span class="sxs-lookup"><span data-stu-id="46d1b-294">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="46d1b-295">對 Unmanaged 端的 Variant 所做的變更，在從呼叫傳回時，會傳播回原始物件。</span><span class="sxs-lookup"><span data-stu-id="46d1b-295">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="46d1b-296">如果 Variant 的類型和傳遞至呼叫的 Variant 類型不同，則變更會傳播回不同類型的物件。</span><span class="sxs-lookup"><span data-stu-id="46d1b-296">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="46d1b-297">也就是說，傳遞至呼叫的物件類型，可以不同於從呼叫傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-297">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>  
  
-   <span data-ttu-id="46d1b-298">以傳址方式將 Variant 傳遞給 Managed 程式碼時，封送處理器會建立新的物件，先將 Variant 的內容複製到物件，再進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="46d1b-298">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="46d1b-299">物件參考會傳遞至 Managed 函式，使用者可在此任意變更物件。</span><span class="sxs-lookup"><span data-stu-id="46d1b-299">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="46d1b-300">對參考的物件所做的任何變更，在從呼叫傳回時，會傳播回原始的 Variant。</span><span class="sxs-lookup"><span data-stu-id="46d1b-300">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="46d1b-301">如果物件的類型和傳遞給呼叫的物件類型不同，原始 Variant 類型就會變更，值也會傳播回 Variant。</span><span class="sxs-lookup"><span data-stu-id="46d1b-301">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="46d1b-302">同樣地，傳遞至呼叫的 Variant 類型，可以不同於從呼叫傳回的 Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-302">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>  
  
 <span data-ttu-id="46d1b-303">**封送處理設有 VT_BYREF 旗標的 Variant 的預設行為**</span><span class="sxs-lookup"><span data-stu-id="46d1b-303">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>  
  
-   <span data-ttu-id="46d1b-304">正以傳值方式傳遞至 Managed 程式碼的 Variant 可設定 **VT_BYREF** 旗標，以表示 Variant 包含的是參考，不是值。</span><span class="sxs-lookup"><span data-stu-id="46d1b-304">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="46d1b-305">如果是這樣，Variant 仍會被封送處理成物件，因為 Variant 正以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="46d1b-305">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="46d1b-306">封送處理器會自動取值 Variant 的內容，並將它先複製到新建立的物件中，再進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="46d1b-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="46d1b-307">然後物件會傳遞到 Managed 函式，但在從呼叫傳回時，該物件不會傳播回原始的 Variant。</span><span class="sxs-lookup"><span data-stu-id="46d1b-307">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="46d1b-308">遺失對 Managed 物件所做的變更。</span><span class="sxs-lookup"><span data-stu-id="46d1b-308">Changes made to the managed object are lost.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="46d1b-309">沒有任何方法可以變更以傳值方式傳遞的 Variant 值，即使 Variant 設定了 **VT_BYREF** 旗標。</span><span class="sxs-lookup"><span data-stu-id="46d1b-309">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>  
  
-   <span data-ttu-id="46d1b-310">正以傳址方式傳遞至 Managed 程式碼的 Variant 也可以設定 **VT_BYREF** 旗標，以表示 Variant 包含另一個參考。</span><span class="sxs-lookup"><span data-stu-id="46d1b-310">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="46d1b-311">如果是這樣，Variant 會被封送處理成 **ref** 物件，因為 Variant 正以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="46d1b-311">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="46d1b-312">封送處理器會自動取值 Variant 的內容，並將它先複製到新建立的物件中，再進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="46d1b-312">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="46d1b-313">在從呼叫傳回時，只有當物件的類型和傳入的物件相同時，物件的值才會傳播回原始 Variant 內的參考。</span><span class="sxs-lookup"><span data-stu-id="46d1b-313">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="46d1b-314">也就是傳播不會變更設有 **VT_BYREF** 旗標的 Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="46d1b-314">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="46d1b-315">如果物件的類型在呼叫期間變更，從呼叫傳回時，就會發生 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="46d1b-315">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>  
  
 <span data-ttu-id="46d1b-316">下表摘要說明 Variant 和物件的傳播規則。</span><span class="sxs-lookup"><span data-stu-id="46d1b-316">The following table summarizes the propagation rules for variants and objects.</span></span>  
  
|<span data-ttu-id="46d1b-317">從</span><span class="sxs-lookup"><span data-stu-id="46d1b-317">From</span></span>|<span data-ttu-id="46d1b-318">以</span><span class="sxs-lookup"><span data-stu-id="46d1b-318">To</span></span>|<span data-ttu-id="46d1b-319">變更傳播回</span><span class="sxs-lookup"><span data-stu-id="46d1b-319">Changes propagated back</span></span>|  
|----------|--------|-----------------------------|  
|<span data-ttu-id="46d1b-320">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="46d1b-320">**Variant**  *v*</span></span>|<span data-ttu-id="46d1b-321">**物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="46d1b-321">**Object**  *o*</span></span>|<span data-ttu-id="46d1b-322">永不</span><span class="sxs-lookup"><span data-stu-id="46d1b-322">Never</span></span>|  
|<span data-ttu-id="46d1b-323">**物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="46d1b-323">**Object**  *o*</span></span>|<span data-ttu-id="46d1b-324">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="46d1b-324">**Variant**  *v*</span></span>|<span data-ttu-id="46d1b-325">永不</span><span class="sxs-lookup"><span data-stu-id="46d1b-325">Never</span></span>|  
|<span data-ttu-id="46d1b-326">**Variant**   ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="46d1b-326">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="46d1b-327">**Ref 物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="46d1b-327">**Ref Object**  *o*</span></span>|<span data-ttu-id="46d1b-328">永遠</span><span class="sxs-lookup"><span data-stu-id="46d1b-328">Always</span></span>|  
|<span data-ttu-id="46d1b-329">**Ref 物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="46d1b-329">**Ref object**  *o*</span></span>|<span data-ttu-id="46d1b-330">**Variant**   ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="46d1b-330">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="46d1b-331">永遠</span><span class="sxs-lookup"><span data-stu-id="46d1b-331">Always</span></span>|  
|<span data-ttu-id="46d1b-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="46d1b-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="46d1b-333">**物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="46d1b-333">**Object**  *o*</span></span>|<span data-ttu-id="46d1b-334">永不</span><span class="sxs-lookup"><span data-stu-id="46d1b-334">Never</span></span>|  
|<span data-ttu-id="46d1b-335">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="46d1b-335">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="46d1b-336">**Ref 物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="46d1b-336">**Ref Object**  *o*</span></span>|<span data-ttu-id="46d1b-337">只有當類型不變更時。</span><span class="sxs-lookup"><span data-stu-id="46d1b-337">Only if the type has not changed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46d1b-338">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46d1b-338">See Also</span></span>  
 [<span data-ttu-id="46d1b-339">預設的封送處理行為</span><span class="sxs-lookup"><span data-stu-id="46d1b-339">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [<span data-ttu-id="46d1b-340">Blittable 和非 Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="46d1b-340">Blittable and Non-Blittable Types</span></span>](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="46d1b-341">方向屬性</span><span class="sxs-lookup"><span data-stu-id="46d1b-341">Directional Attributes</span></span>](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [<span data-ttu-id="46d1b-342">複製和 Pin</span><span class="sxs-lookup"><span data-stu-id="46d1b-342">Copying and Pinning</span></span>](../../../docs/framework/interop/copying-and-pinning.md)
