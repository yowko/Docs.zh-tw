---
title: 物件的預設封送處理
description: 瞭解物件的預設封送處理。 檢查封送處理選項。 將物件封送處理至介面或變數、物件的變體，以及 ByRef 變體。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
ms.openlocfilehash: 7b8f94f4dfd8e8b9e8e04df8de5f8266a8581a92
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618443"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="8dbe7-105">物件的預設封送處理</span><span class="sxs-lookup"><span data-stu-id="8dbe7-105">Default Marshaling for Objects</span></span>

<span data-ttu-id="8dbe7-106">類型為 <xref:System.Object?displayProperty=nameWithType> 的參數和欄位可以向 Unmanaged 程式碼公開為下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="8dbe7-106">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>

- <span data-ttu-id="8dbe7-107">Variant，當物件是參數時。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-107">A variant when the object is a parameter.</span></span>

- <span data-ttu-id="8dbe7-108">介面，當物件是結構欄位時。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-108">An interface when the object is a structure field.</span></span>

<span data-ttu-id="8dbe7-109">只有 COM Interop 支援封送處理物件類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-109">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="8dbe7-110">預設行為是封送處理 COM Variant 的物件。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-110">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="8dbe7-111">這些規則只適用於**物件**類型，不適用於衍生自**物件**類別的強型別物件。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-111">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>

## <a name="marshaling-options"></a><span data-ttu-id="8dbe7-112">封送處理選項</span><span class="sxs-lookup"><span data-stu-id="8dbe7-112">Marshaling Options</span></span>

<span data-ttu-id="8dbe7-113">下表顯示**物件**資料類型的封送處理選項。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-113">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="8dbe7-114"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理物件。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-114">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>

|<span data-ttu-id="8dbe7-115">列舉類型</span><span class="sxs-lookup"><span data-stu-id="8dbe7-115">Enumeration type</span></span>|<span data-ttu-id="8dbe7-116">Unmanaged 格式的描述</span><span class="sxs-lookup"><span data-stu-id="8dbe7-116">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="8dbe7-117">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-117">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="8dbe7-118">(參數預設值)</span><span class="sxs-lookup"><span data-stu-id="8dbe7-118">(default for parameters)</span></span>|<span data-ttu-id="8dbe7-119">COM 樣式的 Variant。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-119">A COM-style variant.</span></span>|
|<span data-ttu-id="8dbe7-120">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-120">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="8dbe7-121">如果可能的話，為 **IDispatch** 介面；否則為 **IUnknown** 介面。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-121">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|
|<span data-ttu-id="8dbe7-122">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-122">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="8dbe7-123">(欄位預設值)</span><span class="sxs-lookup"><span data-stu-id="8dbe7-123">(default for fields)</span></span>|<span data-ttu-id="8dbe7-124">**IUnknown** 介面。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-124">An **IUnknown** interface.</span></span>|
|<span data-ttu-id="8dbe7-125">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-125">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="8dbe7-126">**IDispatch** 介面。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-126">An **IDispatch** interface.</span></span>|

<span data-ttu-id="8dbe7-127">下例顯示 `MarshalObject` 的 Managed 介面定義。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-127">The following example shows the managed interface definition for `MarshalObject`.</span></span>

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

<span data-ttu-id="8dbe7-128">下列程式碼會將 `MarshalObject` 介面匯出至型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-128">The following code exports the `MarshalObject` interface to a type library.</span></span>

```cpp
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
> <span data-ttu-id="8dbe7-129">Interop 封送處理器會呼叫之後，自動釋放 Variant 內所有的配置物件。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-129">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>

<span data-ttu-id="8dbe7-130">下例會顯示格式化的實值型別。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-130">The following example shows a formatted value type.</span></span>

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

<span data-ttu-id="8dbe7-131">下列程式碼會將格式化的類型匯出至型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-131">The following code exports the formatted type to a type library.</span></span>

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a><span data-ttu-id="8dbe7-132">將物件封送處理成介面</span><span class="sxs-lookup"><span data-stu-id="8dbe7-132">Marshaling Object to Interface</span></span>

<span data-ttu-id="8dbe7-133">向 COM 將物件公開為介面時，該介面是 Managed 類型 <xref:System.Object> 的類別介面 (**_Object** 介面)。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-133">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="8dbe7-134">此介面在產生的類型程式庫中會輸入為**IDispatch** （ <xref:System.Runtime.InteropServices.UnmanagedType> ）或**iunknown** （**unmanagedtype.lpwstr iunknown**）。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-134">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="8dbe7-135">COM 用戶端可以動態方式叫用 Managed 類別的成員，或其衍生類別透過 **_Object** 介面所實作的任何成員。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-135">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="8dbe7-136">用戶端也可以呼叫 **QueryInterface** 取得 Managed 類型明確實作的任何其他介面。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-136">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>

## <a name="marshaling-object-to-variant"></a><span data-ttu-id="8dbe7-137">將物件封送處理成 Variant</span><span class="sxs-lookup"><span data-stu-id="8dbe7-137">Marshaling Object to Variant</span></span>

<span data-ttu-id="8dbe7-138">當物件封送處理成 Variant 時，會根據下列規則在執行階段決定內部的 Variant 類型：</span><span class="sxs-lookup"><span data-stu-id="8dbe7-138">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>

- <span data-ttu-id="8dbe7-139">如果物件參考為 null (Visual Basic 為**Nothing**)，物件會封送處理成 **VT_EMPTY** 類型的 Variant。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-139">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>

- <span data-ttu-id="8dbe7-140">如果物件是下表所列任一類型的執行個體，則產生的 Variant 類型是由封送處理器內建的規則決定，並顯示在資料表中。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-140">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>

- <span data-ttu-id="8dbe7-141">需要明確控制封送處理行為的其他物件，可以實作 <xref:System.IConvertible> 介面。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-141">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="8dbe7-142">在此情況下，Variant 類型是由 <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> 方法傳回的類型程式碼所決定。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-142">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8dbe7-143">否則，物件會封送處理成 **VT_UNKNOWN** 類型的 Variant。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-143">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>

### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="8dbe7-144">將系統類型封送處理為 Variant</span><span class="sxs-lookup"><span data-stu-id="8dbe7-144">Marshaling System Types to Variant</span></span>

<span data-ttu-id="8dbe7-145">下表顯示 Managed 物件類型及其對應的 COM Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-145">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="8dbe7-146">只有當正在呼叫的方法簽章是 <xref:System.Object?displayProperty=nameWithType> 類型時，這些類型才會轉換。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-146">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>

|<span data-ttu-id="8dbe7-147">物件類型</span><span class="sxs-lookup"><span data-stu-id="8dbe7-147">Object type</span></span>|<span data-ttu-id="8dbe7-148">COM Variant 類型</span><span class="sxs-lookup"><span data-stu-id="8dbe7-148">COM variant type</span></span>|
|-----------------|----------------------|
|<span data-ttu-id="8dbe7-149">Null 物件參考 (在 Visual Basic 中為 **Nothing**)。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-149">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="8dbe7-150">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-150">**VT_EMPTY**</span></span>|
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-151">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-151">**VT_NULL**</span></span>|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-152">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-152">**VT_ERROR**</span></span>|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-153">**VT_ERROR** 與 **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-153">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-154">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-154">**VT_DISPATCH**</span></span>|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-155">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-155">**VT_UNKNOWN**</span></span>|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-156">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-156">**VT_CY**</span></span>|
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-157">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-157">**VT_BOOL**</span></span>|
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-158">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-158">**VT_I1**</span></span>|
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-159">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-159">**VT_UI1**</span></span>|
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-160">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-160">**VT_I2**</span></span>|
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-161">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-161">**VT_UI2**</span></span>|
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-162">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-162">**VT_I4**</span></span>|
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-163">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-163">**VT_UI4**</span></span>|
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-164">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-164">**VT_I8**</span></span>|
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-165">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-165">**VT_UI8**</span></span>|
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-166">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-166">**VT_R4**</span></span>|
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-167">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-167">**VT_R8**</span></span>|
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-168">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-168">**VT_DECIMAL**</span></span>|
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-169">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-169">**VT_DATE**</span></span>|
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-170">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-170">**VT_BSTR**</span></span>|
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-171">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-171">**VT_INT**</span></span>|
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-172">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-172">**VT_UINT**</span></span>|
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="8dbe7-173">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-173">**VT_ARRAY**</span></span>|

<span data-ttu-id="8dbe7-174">使用前一個範例中定義的 `MarshalObject` 介面，下列程式碼範例示範如何將各種類型的 Variant 傳送到 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-174">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="8dbe7-175">沒有對應 Managed 類型的 COM 類型，可以使用 <xref:System.Runtime.InteropServices.ErrorWrapper>、<xref:System.Runtime.InteropServices.DispatchWrapper>、<xref:System.Runtime.InteropServices.UnknownWrapper> 和 <xref:System.Runtime.InteropServices.CurrencyWrapper> 等包裝函式類別予以封送處理。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-175">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="8dbe7-176">下列程式碼範例示範如何使用這些包裝函式將各種類型的 Variant 傳送到 COM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-176">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="8dbe7-177">包裝函式類別是在 <xref:System.Runtime.InteropServices> 命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-177">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>

### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="8dbe7-178">將 IConvertible 介面封送處理為 Variant</span><span class="sxs-lookup"><span data-stu-id="8dbe7-178">Marshaling the IConvertible Interface to Variant</span></span>

<span data-ttu-id="8dbe7-179">上節中未列出的其他類型，可以透過實作 <xref:System.IConvertible> 介面來控制封送處理的方式。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-179">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="8dbe7-180">如果物件實作 **IConvertible** 介面，從 <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> 方法傳回的 <xref:System.TypeCode> 列舉值會在執行階段決定 COM Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-180">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="8dbe7-181">下表顯示可能的 **TypeCode** 列舉值和每個值對應的 COM Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-181">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>

|<span data-ttu-id="8dbe7-182">TypeCode</span><span class="sxs-lookup"><span data-stu-id="8dbe7-182">TypeCode</span></span>|<span data-ttu-id="8dbe7-183">COM Variant 類型</span><span class="sxs-lookup"><span data-stu-id="8dbe7-183">COM variant type</span></span>|
|--------------|----------------------|
|<span data-ttu-id="8dbe7-184">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-184">**TypeCode.Empty**</span></span>|<span data-ttu-id="8dbe7-185">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-185">**VT_EMPTY**</span></span>|
|<span data-ttu-id="8dbe7-186">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-186">**TypeCode.Object**</span></span>|<span data-ttu-id="8dbe7-187">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-187">**VT_UNKNOWN**</span></span>|
|<span data-ttu-id="8dbe7-188">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-188">**TypeCode.DBNull**</span></span>|<span data-ttu-id="8dbe7-189">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-189">**VT_NULL**</span></span>|
|<span data-ttu-id="8dbe7-190">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-190">**TypeCode.Boolean**</span></span>|<span data-ttu-id="8dbe7-191">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-191">**VT_BOOL**</span></span>|
|<span data-ttu-id="8dbe7-192">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-192">**TypeCode.Char**</span></span>|<span data-ttu-id="8dbe7-193">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-193">**VT_UI2**</span></span>|
|<span data-ttu-id="8dbe7-194">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-194">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="8dbe7-195">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-195">**VT_I1**</span></span>|
|<span data-ttu-id="8dbe7-196">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-196">**TypeCode.Byte**</span></span>|<span data-ttu-id="8dbe7-197">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-197">**VT_UI1**</span></span>|
|<span data-ttu-id="8dbe7-198">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-198">**TypeCode.Int16**</span></span>|<span data-ttu-id="8dbe7-199">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-199">**VT_I2**</span></span>|
|<span data-ttu-id="8dbe7-200">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-200">**TypeCode.UInt16**</span></span>|<span data-ttu-id="8dbe7-201">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-201">**VT_UI2**</span></span>|
|<span data-ttu-id="8dbe7-202">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-202">**TypeCode.Int32**</span></span>|<span data-ttu-id="8dbe7-203">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-203">**VT_I4**</span></span>|
|<span data-ttu-id="8dbe7-204">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-204">**TypeCode.UInt32**</span></span>|<span data-ttu-id="8dbe7-205">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-205">**VT_UI4**</span></span>|
|<span data-ttu-id="8dbe7-206">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-206">**TypeCode.Int64**</span></span>|<span data-ttu-id="8dbe7-207">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-207">**VT_I8**</span></span>|
|<span data-ttu-id="8dbe7-208">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-208">**TypeCode.UInt64**</span></span>|<span data-ttu-id="8dbe7-209">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-209">**VT_UI8**</span></span>|
|<span data-ttu-id="8dbe7-210">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-210">**TypeCode.Single**</span></span>|<span data-ttu-id="8dbe7-211">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-211">**VT_R4**</span></span>|
|<span data-ttu-id="8dbe7-212">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-212">**TypeCode.Double**</span></span>|<span data-ttu-id="8dbe7-213">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-213">**VT_R8**</span></span>|
|<span data-ttu-id="8dbe7-214">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-214">**TypeCode.Decimal**</span></span>|<span data-ttu-id="8dbe7-215">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-215">**VT_DECIMAL**</span></span>|
|<span data-ttu-id="8dbe7-216">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-216">**TypeCode.DateTime**</span></span>|<span data-ttu-id="8dbe7-217">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-217">**VT_DATE**</span></span>|
|<span data-ttu-id="8dbe7-218">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-218">**TypeCode.String**</span></span>|<span data-ttu-id="8dbe7-219">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-219">**VT_BSTR**</span></span>|
|<span data-ttu-id="8dbe7-220">不支援。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-220">Not supported.</span></span>|<span data-ttu-id="8dbe7-221">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-221">**VT_INT**</span></span>|
|<span data-ttu-id="8dbe7-222">不支援。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-222">Not supported.</span></span>|<span data-ttu-id="8dbe7-223">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-223">**VT_UINT**</span></span>|
|<span data-ttu-id="8dbe7-224">不支援。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-224">Not supported.</span></span>|<span data-ttu-id="8dbe7-225">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-225">**VT_ARRAY**</span></span>|
|<span data-ttu-id="8dbe7-226">不支援。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-226">Not supported.</span></span>|<span data-ttu-id="8dbe7-227">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-227">**VT_RECORD**</span></span>|
|<span data-ttu-id="8dbe7-228">不支援。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-228">Not supported.</span></span>|<span data-ttu-id="8dbe7-229">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-229">**VT_CY**</span></span>|
|<span data-ttu-id="8dbe7-230">不支援。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-230">Not supported.</span></span>|<span data-ttu-id="8dbe7-231">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-231">**VT_VARIANT**</span></span>|

<span data-ttu-id="8dbe7-232">COM Variant 的值是透過呼叫 **IConvertible.To** *Type* 介面所決定；其中 **To** *Type* 是轉換常式，對應到從 **IConvertible.GetTypeCode** 傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-232">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="8dbe7-233">例如，從 **IConvertible.GetTypeCode** 傳回 **TypeCode.Double** 的物件，會封送處理成 **VT_R8** 類型的 COM Variant。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-233">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="8dbe7-234">您可以透過轉換為 **IConvertible** 介面及呼叫 <xref:System.IConvertible.ToDouble%2A> 方法，取得 Variant 的值 (儲存在 COM Variant 的 **dblVal** 欄位)。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-234">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>

## <a name="marshaling-variant-to-object"></a><span data-ttu-id="8dbe7-235">將 Variant 封送處理成物件</span><span class="sxs-lookup"><span data-stu-id="8dbe7-235">Marshaling Variant to Object</span></span>

<span data-ttu-id="8dbe7-236">將 Variant 封送處理成物件時，已封送處理的 Variant 類型 (有時是值)，可以判斷所產生的物件類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-236">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="8dbe7-237">下表可以識別當 Variant 從 COM 傳遞至 .NET ＦFramework 時，封送處理器建立的每個 Variant 類型和對應的物件類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-237">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>

|<span data-ttu-id="8dbe7-238">COM Variant 類型</span><span class="sxs-lookup"><span data-stu-id="8dbe7-238">COM variant type</span></span>|<span data-ttu-id="8dbe7-239">物件類型</span><span class="sxs-lookup"><span data-stu-id="8dbe7-239">Object type</span></span>|
|----------------------|-----------------|
|<span data-ttu-id="8dbe7-240">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-240">**VT_EMPTY**</span></span>|<span data-ttu-id="8dbe7-241">Null 物件參考 (在 Visual Basic 中為 **Nothing**)。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-241">Null object reference (**Nothing** in Visual Basic).</span></span>|
|<span data-ttu-id="8dbe7-242">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-242">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-243">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-243">**VT_DISPATCH**</span></span>|<span data-ttu-id="8dbe7-244">**System.__ComObject** or null if (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="8dbe7-244">**System.__ComObject** or null if (pdispVal == null)</span></span>|
|<span data-ttu-id="8dbe7-245">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-245">**VT_UNKNOWN**</span></span>|<span data-ttu-id="8dbe7-246">**System.__ComObject** or null if (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="8dbe7-246">**System.__ComObject** or null if (punkVal == null)</span></span>|
|<span data-ttu-id="8dbe7-247">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-247">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-248">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-248">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-249">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-249">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-250">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-250">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-251">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-251">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-252">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-252">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-253">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-253">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-254">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-254">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-255">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-255">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-256">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-256">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-257">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-257">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-258">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-258">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-259">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-259">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-260">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-260">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-261">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-261">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-262">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-262">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-263">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-263">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-264">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="8dbe7-264">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-265">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-265">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="8dbe7-266">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-266">**VT_RECORD**</span></span>|<span data-ttu-id="8dbe7-267">對應 Boxed 實值型別。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-267">Corresponding boxed value type.</span></span>|
|<span data-ttu-id="8dbe7-268">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-268">**VT_VARIANT**</span></span>|<span data-ttu-id="8dbe7-269">不支援。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-269">Not supported.</span></span>|

<span data-ttu-id="8dbe7-270">從 COM 傳遞至 Managed 程式碼再回到 COM 的 Variant 類型，在呼叫期間可能不會保留相同的 Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-270">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="8dbe7-271">當 **VT_DISPATCH** 類型的 Variant 從 COM 傳遞至 .NET Framework 時，請考慮會發生什麼情況。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-271">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="8dbe7-272">在封送處理期間，Variant 會轉換成 <xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-272">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8dbe7-273">如果接著將**物件**傳送回 COM，它會封送處理回 **VT_UNKNOWN** 類型的 Variant。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-273">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="8dbe7-274">當物件從 Managed 程式碼封送處理到 COM 時產生的 Variant，不保證和最初用來產生物件的 Variant 是同一類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-274">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>

## <a name="marshaling-byref-variants"></a><span data-ttu-id="8dbe7-275">封送處理 ByRef Variant</span><span class="sxs-lookup"><span data-stu-id="8dbe7-275">Marshaling ByRef Variants</span></span>

<span data-ttu-id="8dbe7-276">雖然 Variant 本身可以傳值方式或傳址方式傳遞，**VT_BYREF** 旗標也可搭配任何 Variant 類型使用來表示 Variant 的內容正在以傳址方式傳遞，不是以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-276">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="8dbe7-277">以傳址方式封送處理的 Variant 和封送處理設有 **VT_BYREF** 旗標的 Variant 之間的差異，會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-277">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="8dbe7-278">下圖將釐清這些差異：</span><span class="sxs-lookup"><span data-stu-id="8dbe7-278">The following illustration clarifies the differences:</span></span>

<span data-ttu-id="8dbe7-279">![顯示堆疊上傳遞的變數的圖表。](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span><span class="sxs-lookup"><span data-stu-id="8dbe7-279">![Diagram that shows variant passed on the stack.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span></span>
<span data-ttu-id="8dbe7-280">以傳值方式傳遞和以傳址方式傳遞的 Variant</span><span class="sxs-lookup"><span data-stu-id="8dbe7-280">Variants passed by value and by reference</span></span>

<span data-ttu-id="8dbe7-281">**依值封送處理物件和 Variant 的預設行為**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-281">**Default behavior for marshaling objects and variants by value**</span></span>

- <span data-ttu-id="8dbe7-282">當從 Managed 程式碼將物件傳送至 COM 時，會使用[將物件封送處理成 Variant](#marshaling-object-to-variant) 中定義的規則，將物件的內容複製到封送處理器所建立的新 Variant 中。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-282">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="8dbe7-283">對 Unmanaged 端的 Variant 所做的變更，在從呼叫傳回時，不會傳播回原始物件。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-283">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>

- <span data-ttu-id="8dbe7-284">當從 COM 將 Variant 傳送至 Managed 程式碼時，會使用[將 Variant 封送處理成物件](#marshaling-variant-to-object)中定義的規則，將 Variant 的內容複製到新建立的物件中。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-284">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="8dbe7-285">對 Unmanaged 端的 Variant 所做的變更，在從呼叫傳回時，不會傳播回原始物件。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-285">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>

<span data-ttu-id="8dbe7-286">**依參考封送處理物件和 Variant 的預設行為**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-286">**Default behavior for marshaling objects and variants by reference**</span></span>

<span data-ttu-id="8dbe7-287">若要將變更傳播回呼叫端，必須以傳址方式傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-287">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="8dbe7-288">例如，您可以在 C# 中使用 **ref** 關鍵字 (或在 Visual Basic 的 Managed 程式碼中使用 **ByRef**)，以傳址方式傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-288">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="8dbe7-289">在 COM 中，參考參數是使用 **Variant \*** 等指標傳遞。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-289">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>

- <span data-ttu-id="8dbe7-290">以傳址方式將物件傳遞給 COM 時，封送處理器會建立新的 Variant，先將物件參考的內容複製到 Variant，再進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-290">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="8dbe7-291">Variant 會傳遞至 Unmanaged 函式，使用者可在此任意變更 Variant 的內容。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-291">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="8dbe7-292">對 Unmanaged 端的 Variant 所做的變更，在從呼叫傳回時，會傳播回原始物件。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-292">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="8dbe7-293">如果 Variant 的類型和傳遞至呼叫的 Variant 類型不同，則變更會傳播回不同類型的物件。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-293">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="8dbe7-294">也就是說，傳遞至呼叫的物件類型，可以不同於從呼叫傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-294">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>

- <span data-ttu-id="8dbe7-295">以傳址方式將 Variant 傳遞給 Managed 程式碼時，封送處理器會建立新的物件，先將 Variant 的內容複製到物件，再進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-295">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="8dbe7-296">物件參考會傳遞至 Managed 函式，使用者可在此任意變更物件。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-296">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="8dbe7-297">對參考的物件所做的任何變更，在從呼叫傳回時，會傳播回原始的 Variant。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-297">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="8dbe7-298">如果物件的類型和傳遞給呼叫的物件類型不同，原始 Variant 類型就會變更，值也會傳播回 Variant。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-298">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="8dbe7-299">同樣地，傳遞至呼叫的 Variant 類型，可以不同於從呼叫傳回的 Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-299">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>

 <span data-ttu-id="8dbe7-300">**封送處理設有 VT_BYREF 旗標的 Variant 的預設行為**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-300">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>

- <span data-ttu-id="8dbe7-301">正以傳值方式傳遞至 Managed 程式碼的 Variant 可設定 **VT_BYREF** 旗標，以表示 Variant 包含的是參考，不是值。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-301">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="8dbe7-302">如果是這樣，Variant 仍會被封送處理成物件，因為 Variant 正以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-302">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="8dbe7-303">封送處理器會自動取值 Variant 的內容，並將它先複製到新建立的物件中，再進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-303">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="8dbe7-304">然後物件會傳遞到 Managed 函式，但在從呼叫傳回時，該物件不會傳播回原始的 Variant。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-304">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="8dbe7-305">遺失對 Managed 物件所做的變更。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-305">Changes made to the managed object are lost.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="8dbe7-306">沒有任何方法可以變更以傳值方式傳遞的 Variant 值，即使 Variant 設定了 **VT_BYREF** 旗標。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-306">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>

- <span data-ttu-id="8dbe7-307">正以傳址方式傳遞至 Managed 程式碼的 Variant 也可以設定 **VT_BYREF** 旗標，以表示 Variant 包含另一個參考。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-307">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="8dbe7-308">如果是這樣，Variant 會被封送處理成 **ref** 物件，因為 Variant 正以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-308">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="8dbe7-309">封送處理器會自動取值 Variant 的內容，並將它先複製到新建立的物件中，再進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-309">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="8dbe7-310">在從呼叫傳回時，只有當物件的類型和傳入的物件相同時，物件的值才會傳播回原始 Variant 內的參考。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-310">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="8dbe7-311">也就是傳播不會變更設有 **VT_BYREF** 旗標的 Variant 類型。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-311">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="8dbe7-312">如果物件的類型在呼叫期間變更，從呼叫傳回時，就會發生 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-312">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>

<span data-ttu-id="8dbe7-313">下表摘要說明 Variant 和物件的傳播規則。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-313">The following table summarizes the propagation rules for variants and objects.</span></span>

|<span data-ttu-id="8dbe7-314">從</span><span class="sxs-lookup"><span data-stu-id="8dbe7-314">From</span></span>|<span data-ttu-id="8dbe7-315">至</span><span class="sxs-lookup"><span data-stu-id="8dbe7-315">To</span></span>|<span data-ttu-id="8dbe7-316">變更傳播回</span><span class="sxs-lookup"><span data-stu-id="8dbe7-316">Changes propagated back</span></span>|
|----------|--------|-----------------------------|
|<span data-ttu-id="8dbe7-317">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="8dbe7-317">**Variant**  *v*</span></span>|<span data-ttu-id="8dbe7-318">**物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="8dbe7-318">**Object**  *o*</span></span>|<span data-ttu-id="8dbe7-319">永不</span><span class="sxs-lookup"><span data-stu-id="8dbe7-319">Never</span></span>|
|<span data-ttu-id="8dbe7-320">**物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="8dbe7-320">**Object**  *o*</span></span>|<span data-ttu-id="8dbe7-321">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="8dbe7-321">**Variant**  *v*</span></span>|<span data-ttu-id="8dbe7-322">永不</span><span class="sxs-lookup"><span data-stu-id="8dbe7-322">Never</span></span>|
|<span data-ttu-id="8dbe7-323">**Variant** \*\**\*\*\*\*\*pv*     </span><span class="sxs-lookup"><span data-stu-id="8dbe7-323">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="8dbe7-324">**Ref 物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="8dbe7-324">**Ref Object**  *o*</span></span>|<span data-ttu-id="8dbe7-325">永遠</span><span class="sxs-lookup"><span data-stu-id="8dbe7-325">Always</span></span>|
|<span data-ttu-id="8dbe7-326">**Ref 物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="8dbe7-326">**Ref object**  *o*</span></span>|<span data-ttu-id="8dbe7-327">**Variant** \*\**\*\*\*\*\*pv*     </span><span class="sxs-lookup"><span data-stu-id="8dbe7-327">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="8dbe7-328">永遠</span><span class="sxs-lookup"><span data-stu-id="8dbe7-328">Always</span></span>|
|<span data-ttu-id="8dbe7-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="8dbe7-330">**物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="8dbe7-330">**Object**  *o*</span></span>|<span data-ttu-id="8dbe7-331">永不</span><span class="sxs-lookup"><span data-stu-id="8dbe7-331">Never</span></span>|
|<span data-ttu-id="8dbe7-332">**Variant**  *v* **（VT_BYREF** *&#124;* **VT_）**</span><span class="sxs-lookup"><span data-stu-id="8dbe7-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="8dbe7-333">**Ref 物件**  *o*</span><span class="sxs-lookup"><span data-stu-id="8dbe7-333">**Ref Object**  *o*</span></span>|<span data-ttu-id="8dbe7-334">只有當類型不變更時。</span><span class="sxs-lookup"><span data-stu-id="8dbe7-334">Only if the type has not changed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8dbe7-335">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dbe7-335">See also</span></span>

- [<span data-ttu-id="8dbe7-336">預設的封送處理行為</span><span class="sxs-lookup"><span data-stu-id="8dbe7-336">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="8dbe7-337">Blittable 和非 Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="8dbe7-337">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="8dbe7-338">[方向屬性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8dbe7-338">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="8dbe7-339">複製和 Pin</span><span class="sxs-lookup"><span data-stu-id="8dbe7-339">Copying and Pinning</span></span>](copying-and-pinning.md)
