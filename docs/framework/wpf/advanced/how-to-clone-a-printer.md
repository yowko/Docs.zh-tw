---
title: 如何：複製印表機
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
ms.openlocfilehash: 8f3a9c3b4d9f4bcbe3a6ffcff9868aa7b19b8f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544192"
---
# <a name="how-to-clone-a-printer"></a>如何：複製印表機
大部分的企業，在某個時間點，購買多台印表機的相同模型。 一般而言，這些所有在安裝有幾乎相同的組態設定。 安裝每一部印表機可能會很費時而且容易產生錯誤。 <xref:System.Printing.IndexedProperties?displayProperty=nameWithType>命名空間和<xref:System.Printing.PrintServer.InstallPrintQueue%2A>都會以 Microsoft.NET Framework 公開的類別會讓您能夠立即安裝任何數目的其他列印佇列，就會遭到複製，從現有的列印佇列。  
  
## <a name="example"></a>範例  
 在下列範例中，第二個列印佇列會複製從現有的列印佇列。 第二個後者只能在其名稱、 位置、 連接埠，以及共用的狀態。 執行此作業的主要步驟如下所示。  
  
1.  建立<xref:System.Printing.PrintQueue>現有印表機即將複製的物件。  
  
2.  建立<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>從<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>的<xref:System.Printing.PrintQueue>。 <xref:System.Collections.DictionaryEntry.Value%2A>此字典中的每個項目的屬性是物件的其中一個衍生自類型<xref:System.Printing.IndexedProperties.PrintProperty>。 有兩種方式，在此字典中設定的項目值。  
  
    -   使用此字典**移除**和<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A>方法來移除該項目，然後重新加入想要的值。  
  
    -   使用此字典<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A>方法。  
  
     下列範例會示範這兩種方式。  
  
3.  建立<xref:System.Printing.IndexedProperties.PrintBooleanProperty>物件，並設定其<xref:System.Printing.IndexedProperties.PrintProperty.Name%2A>"IsShared 」 至及其<xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A>至`true`。  
  
4.  使用<xref:System.Printing.IndexedProperties.PrintBooleanProperty>物件的值<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>的"IsShared"項目。  
  
5.  建立<xref:System.Printing.IndexedProperties.PrintStringProperty>物件，並設定其<xref:System.Printing.IndexedProperties.PrintProperty.Name%2A>至 「 共用 」 的名稱和其<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>適當<xref:System.String>。  
  
6.  使用<xref:System.Printing.IndexedProperties.PrintStringProperty>物件的值<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>的 」 共用名稱"項目。  
  
7.  建立另一個<xref:System.Printing.IndexedProperties.PrintStringProperty>物件，並設定其<xref:System.Printing.IndexedProperties.PrintProperty.Name%2A>至 「 位置 」 和其<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>適當<xref:System.String>。  
  
8.  使用第二個<xref:System.Printing.IndexedProperties.PrintStringProperty>物件的值<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>的 「 位置 」 項目。  
  
9. 建立陣列<xref:System.String>s。 每個項目是在伺服器上的連接埠的名稱。  
  
10. 使用<xref:System.Printing.PrintServer.InstallPrintQueue%2A>安裝新印表機的新值。  
  
 以下是範例。  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)
