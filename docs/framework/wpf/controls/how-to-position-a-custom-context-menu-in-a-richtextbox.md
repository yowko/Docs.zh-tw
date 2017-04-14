---
title: "如何：在 RichTextBox 中放置自訂內容功能表 | Microsoft Docs"
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
  - "自訂內容功能表定位"
  - "定位自訂內容功能表"
  - "RichTextBox 控制項中，定位自訂內容功能表"
  - "定位的內容功能表"
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：在 RichTextBox 中放置自訂內容功能表
這個範例示範如何將自訂內容功能表<xref:System.Windows.Controls.RichTextBox>。  
  
 當您實作的自訂內容功能表**RichTextBox**，您必須負責處理內容功能表中的位置。  根據預設，自訂內容功能表開啟中間的**RichTextBox**。  
  
## <a name="example"></a>範例  
 若要覆寫預設放置行為，將新增的接聽程式<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>事件。  下列範例示範如何以程式設計方式執行這項操作。  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>範例  
 下列範例會示範實作對應<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>事件接聽程式。  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>另請參閱  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)