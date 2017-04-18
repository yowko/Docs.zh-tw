---
title: "Blittable 和非 Blittable 類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "blittable 類型, Interop 封送處理"
  - "Interop 封送處理, blittable 類型"
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# Blittable 和非 Blittable 類型
大部分的資料型別在 Managed 和 Unmanaged 記憶體中都有共同的表示，而且不需要透過 Interop 封送處理器的特殊處理。  這些型別稱為「*Blittable 型別*」\(Blittable Type\)，因為在 Managed 和 Unmanaged 程式碼之間傳遞時，這個型別並不需要進行轉換。  
  
 從平台叫用呼叫傳回的結構必須是 Blittable 型別。  平台叫用不支援非 Blittable 結構做為傳回型別。  
  
 下列 <xref:System> 命名空間中的型別是 Blittable 型別：  
  
-   <xref:System.Byte?displayProperty=fullName>  
  
-   <xref:System.SByte?displayProperty=fullName>  
  
-   <xref:System.Int16?displayProperty=fullName>  
  
-   <xref:System.UInt16?displayProperty=fullName>  
  
-   <xref:System.Int32?displayProperty=fullName>  
  
-   <xref:System.UInt32?displayProperty=fullName>  
  
-   <xref:System.Int64?displayProperty=fullName>  
  
-   <xref:System.UInt64?displayProperty=fullName>  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Single?displayProperty=fullName>  
  
-   <xref:System.Double?displayProperty=fullName>  
  
 以下的複雜型別也是 Blittable 型別：  
  
-   Blittable 型別的一維陣列，例如整數陣列。  然而，包含 Blittable 型別之可變陣列的型別本身，則不是 Blittable。  
  
-   格式化的值型別，其中只包含 Blittable 型別 \(以及類別，如果被封送處理成格式化型別\)。  如需格式化的值型別詳細資訊，請參閱[Default Marshaling for Value Types](http://msdn.microsoft.com/zh-tw/4d9a876c-e05a-40ba-bd85-bd22877f984a)。  
  
 物件參考不會是 Blittable。  這些參考包括本身為 Blittable 之物件的參考陣列。  例如，您可以定義本身為 Blittable 的結構，卻不能定義包含這些結構之參考陣列的 Blittable 型別。  
  
 因為是最佳化，所以在封送處理時，只包含 Blittable 成員的 Blittable 型別和類別之陣列，會被 [Pin](../../../docs/framework/interop/copying-and-pinning.md) 而不會被複製。  當呼叫端和被呼叫端是在相同的 Apartment 時，這些型別可以封送處理為 In\/Out 參數。  但是這些型別實際上會封送處理為 In 參數，而且如果您要將引數封送處理為 In\/Out 參數，就必須套用 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 屬性。  
  
 部分 Managed 資料型別，在 Unmanaged 環境中需要不同的表示式。  這些非 Blittable 資料型別必須轉換成可以封送處理的格式。  例如，Managed 字串是非 Blittable 型別，因為必須轉換成字串物件才能封送處理。  
  
 下表列出 <xref:System> 命名空間的非 Blittable 型別。  [委派](http://msdn.microsoft.com/zh-tw/d176ee76-f982-494b-b03d-92e4118896e2)是一種參考靜態方法或類別執行個體的資料結構，也是非 Blittable。  
  
|非 Blittable 型別|描述|  
|--------------------|--------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|轉換成 C\-Style 陣列，或 `SAFEARRAY`。|  
|[System.Boolean](http://msdn.microsoft.com/zh-tw/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)|轉換為 1、2 或 4 個位元組值，而 `true` 為 1 或 \-1。|  
|[System.Char](http://msdn.microsoft.com/zh-tw/cecc87c1-075e-4cde-aa56-33d189f66feb)|轉換為 Unicode 或 ANSI 字元。|  
|[System.Class](http://msdn.microsoft.com/zh-tw/fe334af5-0123-43d8-be84-26f6f023ddb6)|轉換為類別介面。|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|轉換為 Variant 或介面。|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|轉換成 C\-Style 陣列，或 `SAFEARRAY`。|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|將 null 參考中的字串結尾轉換成 BSTR。|  
|[System.Valuetype](http://msdn.microsoft.com/zh-tw/4d9a876c-e05a-40ba-bd85-bd22877f984a)|轉換為具有固定記憶體配置的結構。|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|轉換成 C\-Style 陣列，或 `SAFEARRAY`。|  
  
 類別和物件型別只受到 COM Interop 的支援。  如需 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C\# 及 C\+\+ 中對應的型別，請參閱 [類別庫概觀](../../../docs/standard/class-library-overview.md)。  
  
## 請參閱  
 [預設的封送處理行為](../../../docs/framework/interop/default-marshaling-behavior.md)