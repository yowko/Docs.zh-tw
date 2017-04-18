---
title: "類型等價和內嵌 Interop 類型 | Microsoft Docs"
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
  - "內嵌的 Interop 類型"
  - "NoPIA"
  - "主要 Interop 組件, 在 CLR 第 4 版中非必要"
  - "類型等價"
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# 類型等價和內嵌 Interop 類型
從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，Common Language Runtime 就支援將 COM 型別的型別資訊直接內嵌在 Managed 組件中，而不需要讓 Managed 組件從 Interop 組件中取得 COM 型別的型別資訊。  因為內嵌的型別資訊只包括 Managed 組件實際使用的型別和成員，所以兩個 Managed 組件可能會對相同的 COM 型別具有非常不同的檢視。  每個 Managed 組件都具有不同的 <xref:System.Type> 物件來代表其 COM 型別的檢視。  Common Language Runtime 支援這些介面、結構、列舉和委派之不同檢視之間的型別等價。  
  
 型別等價是指從某個 Managed 組件傳遞給另一個組件的 COM 物件可以轉換成接收組件中的適當 Managed 型別。  
  
> [!NOTE]
>  型別等價和內嵌的 Interop 型別會簡化使用 COM 元件之應用程式和增益集的部署作業，因為您不需要使用應用程式來部署 Interop 組件。  如果共用 COM 元件的開發人員想要讓其元件能夠由舊版 .NET Framework 使用，他們仍然必須建立主要 Interop 組件 \(PIA\)。  
  
## 型別等價  
 COM 型別的等價支援介面、結構、列舉和委派。  如果下列條件都成立，COM 型別就會限定為相等：  
  
-   兩個型別都是介面、結構、列舉或委派。  
  
-   型別具有相同的識別，如下一節所述。  
  
-   兩個型別都適用於型別等價，如[將 COM 型別標記為型別等價](#type_equiv)一節所述。  
  
### 型別識別  
 當兩個型別的範圍和識別相符時，它們就會被判斷為具有相同的識別。換言之，它們都具有 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性 \(Attribute\)，而且這兩個屬性具有相符的 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 和 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> 屬性 \(Property\)。  <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 的比較不區分大小寫。  
  
 如果某個型別沒有 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性，或者它具有未指定範圍和識別項的 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性，此型別仍然可以被視為等價，如下所示：  
  
-   若為介面，就會使用 <xref:System.Runtime.InteropServices.GuidAttribute> 的值而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=fullName> 屬性，而且使用 <xref:System.Type.FullName%2A?displayProperty=fullName> 屬性 \(亦即，型別名稱，包括命名空間\) 而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=fullName> 屬性。  
  
-   若為結構、列舉和委派，就會使用包含組件的 <xref:System.Runtime.InteropServices.GuidAttribute> 而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 屬性，而且使用 <xref:System.Type.FullName%2A?displayProperty=fullName> 屬性而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> 屬性。  
  
<a name="type_equiv"></a>   
### 將 COM 型別標記為型別等價  
 您可以用兩種方式，將型別標記為適用於型別等價：  
  
-   將 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性套用至型別。  
  
-   讓型別成為 COM 匯入型別。  如果介面具有 <xref:System.Runtime.InteropServices.ComImportAttribute> 屬性，它就是 COM 匯入型別。  如果用來定義介面、結構、列舉或委派的組件具有 <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> 屬性，它就是 COM 匯入型別。  
  
## 請參閱  
 <xref:System.Type.IsEquivalentTo%2A>   
 [Using COM Types in Managed Code](http://msdn.microsoft.com/zh-tw/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)   
 [匯入類型程式庫做為組件](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)