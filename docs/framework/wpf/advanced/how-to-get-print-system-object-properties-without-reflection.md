---
title: HOW TO：取得列印系統物件屬性但不使用反映
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: bb906dafd98e75708764b5f0f009900719f6a475
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335195"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a>HOW TO：取得列印系統物件屬性但不使用反映
使用反映來詳細列出的物件上的屬性 （和這些屬性的類型） 可能會降低應用程式的效能。 <xref:System.Printing.IndexedProperties>命名空間提供一個方法來取得這項資訊搭配使用反映。  
  
## <a name="example"></a>範例  
 執行此動作的步驟如下所示。  
  
1. 建立型別的執行個體。 在下列範例中，類型是<xref:System.Printing.PrintQueue>隨附於 Microsoft.NET Framework，但幾乎完全相同的程式碼的類型應該適用於類型衍生自<xref:System.Printing.PrintSystemObject>。  
  
2. 建立<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>的型別<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>。 <xref:System.Collections.DictionaryEntry.Value%2A>這個字典中的每個項目屬性是其中一個衍生自型別的物件<xref:System.Printing.IndexedProperties.PrintProperty>。  
  
3. 列舉成員的字典。 為每個，請執行下列項目。  
  
4. 向上轉型至每個項目的值<xref:System.Printing.IndexedProperties.PrintProperty>並使用它來建立<xref:System.Printing.IndexedProperties.PrintProperty>物件。  
  
5. 取得的型別<xref:System.Printing.IndexedProperties.PrintProperty.Value%2A>的每個<xref:System.Printing.IndexedProperties.PrintProperty>物件。  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
