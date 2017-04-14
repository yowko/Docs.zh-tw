---
title: "如何：取得列印系統物件屬性但不使用反映 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PrintSystemObject, 取得屬性"
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：取得列印系統物件屬性但不使用反映
使用反映將物件上的屬性 \(和這些屬性的型別\) 項目化，會降低應用程式的效能。  <xref:System.Printing.IndexedProperties> 命名空間提供了一種利用反映取得這項資訊的方法。  
  
## 範例  
 這項作業的步驟如下。  
  
1.  建立型別的執行個體。  在下列範例中，這個型別是隨 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 提供的 <xref:System.Printing.PrintQueue>，但是相同的程式碼只要做少許修改，應該也適用於您從 <xref:System.Printing.PrintSystemObject> 衍生而來的型別。  
  
2.  從型別的 <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> 建立 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>。  在這個字典中，每個項目的 <xref:System.Collections.DictionaryEntry.Value%2A> 屬性各代表從 <xref:System.Printing.IndexedProperties.PrintProperty> 衍生的其中一個型別的物件。  
  
3.  列舉字典的成員。  針對每一個成員執行下列步驟。  
  
4.  將每個項目值向上轉型為 <xref:System.Printing.IndexedProperties.PrintProperty>，並用它建立 <xref:System.Printing.IndexedProperties.PrintProperty> 物件。  
  
5.  取得 <xref:System.Printing.IndexedProperties.PrintProperty> 物件的各 <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> 的型別。  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## 請參閱  
 <xref:System.Printing.IndexedProperties.PrintProperty>   
 <xref:System.Printing.PrintSystemObject>   
 <xref:System.Printing.IndexedProperties>   
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>   
 <xref:System.Printing.LocalPrintServer>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Collections.DictionaryEntry>   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)