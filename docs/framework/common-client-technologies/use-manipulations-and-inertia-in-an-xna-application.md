---
title: "Using Manipulations and Inertia in an XNA Application | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# Using Manipulations and Inertia in an XNA Application
本文說明如何在 Microsoft XNA 應用程式中使用操作和慣性處理，來控制遊戲個件的移動。  在閱讀本文之前，您應該先熟悉[Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)主題和基本 XNA 程式設計概念。  
  
 若要執行本文所述的工作，您的 XNA 專案必須參考  <xref:System.Windows.Input.Manipulations> 組件，且您的電腦上必須已安裝 [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) \([下載](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)\)，以便您的專案可以參考 XNA 組件。  
  
## 功能概觀  
 本文示範如何建立代表使用操作和慣性處理之遊戲個件的自訂類別。  這個類別可讓您透過使用滑鼠拖曳再放開的方式，在畫面上操作遊戲個件。  放開滑鼠之後，慣性處理會讓遊戲個件保持移動，但速度會逐漸變慢。  移動方式包括線性移動和角度移動。  
  
 ![簡單的操作和慣性應用。](../../../docs/framework/common-client-technologies/media/ndp-gamexna.png "NDP\_GameXna")  
  
 此外，您可以建立管理多個遊戲個件的自訂集合。  這樣做會簡化 XNA Game 類別所需的處理。  
  
 [Creating the GamePiece Class](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [Creating the Game1 Class](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [Full Code Listings](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## 請參閱  
 <xref:System.Windows.Input.Manipulations>   
 [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)