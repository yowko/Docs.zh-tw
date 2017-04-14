---
title: "如何：複製印表機 | Microsoft Docs"
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
  - "複製列印佇列"
  - "複製印表機"
  - "列印佇列"
  - "列印佇列, 複製"
  - "印表機, 複製"
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：複製印表機
大部分公司有時會購買多部相同機型的印表機。  一般而言，這些都會使用虛擬上相同的組態設定來進行安裝。  而安裝每部印表機十分耗時而且容易產生錯誤。  使用 [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] 公開的 <xref:System.Printing.IndexedProperties?displayProperty=fullName> 命名空間和 <xref:System.Printing.PrintServer.InstallPrintQueue%2A> 類別，可以立即安裝從現有列印佇列複製 \(Clone\) 的任何數目的額外列印佇列。  
  
## 範例  
 在下面範例中，第二個列印佇列是從現有列印佇列複製而來。  第二個列印佇列與第一個列印佇列的差別只有在於名稱、位置、連接埠和共用狀態。  這個作業的主要步驟如下：  
  
1.  建立要複製之現有印表機的 <xref:System.Printing.PrintQueue> 物件。  
  
2.  從 <xref:System.Printing.PrintQueue> 的 <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> 建立 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>。  在這個字典中，每個項目的 <xref:System.Collections.DictionaryEntry.Value%2A> 屬性各代表從 <xref:System.Printing.IndexedProperties.PrintProperty> 衍生的其中一個型別的物件。  有兩種方式可以在這個字典中設定項目值。  
  
    -   使用字典的 **Remove** 和 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> 方法移除項目，然後使用所要的值重新加入項目。  
  
    -   使用字典的 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> 方法。  
  
     下列範例會示範這兩種方式。  
  
3.  建立 <xref:System.Printing.IndexedProperties.PrintBooleanProperty> 物件，並將它的 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> 設定為 "IsShared"，以及將它的 <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> 設定為 `true`。  
  
4.  使用 <xref:System.Printing.IndexedProperties.PrintBooleanProperty> 物件做為 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> 的 "IsShared" 項目值。  
  
5.  建立 <xref:System.Printing.IndexedProperties.PrintStringProperty> 物件，並將它的 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> 設定為 "ShareName"，以及將它的 <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> 設定為適當 <xref:System.String>。  
  
6.  使用 <xref:System.Printing.IndexedProperties.PrintStringProperty> 物件做為 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> 的 "ShareName" 項目值。  
  
7.  建立另一個 <xref:System.Printing.IndexedProperties.PrintStringProperty> 物件，並將它的 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> 設定為 "Location"，以及將它的 <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> 設定為適當 <xref:System.String>。  
  
8.  使用第二個 <xref:System.Printing.IndexedProperties.PrintStringProperty> 物件做為 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> 的 "Location" 項目值。  
  
9. 建立 <xref:System.String> 的陣列。  每個項目都是伺服器上的連接埠名稱。  
  
10. 使用 <xref:System.Printing.PrintServer.InstallPrintQueue%2A>，以利用新的值安裝新的印表機。  
  
 範例如下。  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## 請參閱  
 <xref:System.Printing.IndexedProperties>   
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>   
 <xref:System.Printing.LocalPrintServer>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Collections.DictionaryEntry>   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)