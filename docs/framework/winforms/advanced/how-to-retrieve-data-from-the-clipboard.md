---
title: "如何：從剪貼簿擷取資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "剪貼簿, 擷取資料"
  - "貼上剪貼簿資料"
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：從剪貼簿擷取資料
<xref:System.Windows.Forms.Clipboard> 類別提供了一些方法，可以用來與 Windows 作業系統的剪貼簿功能互動。  許多應用程式都將剪貼簿當做資料的暫時儲存機制。  例如，文書處理器在進行剪下和貼上作業時就會使用剪貼簿。  剪貼簿也非常適合用來將資料從一個應用程式傳送到另一個應用程式。  
  
 有些應用程式會將資料以多種格式儲存在剪貼簿上，以增加其他可能使用這些資料的應用程式數目。  剪貼簿檔案格式是一個用來辨識格式的字串。  使用所辨識之格式的應用程式可以從剪貼簿擷取相關聯的資料。  <xref:System.Windows.Forms.DataFormats> 類別會提供預先定義的格式名稱，以供您使用。  您也可以使用自己的格式名稱，或將某個物件的型別當做其格式使用。  如需將資料加入至剪貼簿的詳細資訊，請參閱 [如何：將資料加入至剪貼簿](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)。  
  
 若要判斷剪貼簿是否包含特定格式的資料，請使用其中一個 `Contains`*Format* 方法或 <xref:System.Windows.Forms.Clipboard.GetData%2A> 方法。  若要從剪貼簿擷取資料，則請使用其中一個 `Get`*Format* 方法或 <xref:System.Windows.Forms.Clipboard.GetData%2A> 方法。  這些是 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]中的新方法。  
  
 若要使用 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 之前的版本從剪貼簿擷取資料，請使用 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 方法並呼叫所傳回之 <xref:System.Windows.Forms.IDataObject> 的方法。  例如，若要判斷傳回的物件中是否包含特定格式，請呼叫 <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> 方法。  
  
> [!NOTE]
>  所有 Windows 應用程式都會共用系統剪貼簿。  因此，剪貼簿的內容會根據您切換至不同的應用程式而改變。  
>   
>  <xref:System.Windows.Forms.Clipboard> 類別只能用在設定為單一執行緒 Apartment \(STA\) 模式的執行緒中。  若要使用這個類別，請確定 `Main` 方法已使用 <xref:System.STAThreadAttribute> 屬性加以標記。  
  
### 若要以單一且通用的格式從剪貼簿擷取資料  
  
1.  請使用 <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>、<xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>、<xref:System.Windows.Forms.Clipboard.GetImage%2A> 或 <xref:System.Windows.Forms.Clipboard.GetText%2A> 方法。  或者，請先使用對應的 `Contains`*Format* 方法來判斷資料是否為特定格式。  這些方法只能在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]中取得。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### 若要以自訂的格式從剪貼簿擷取資料  
  
1.  請使用具有自訂格式名稱的 <xref:System.Windows.Forms.Clipboard.GetData%2A> 方法。  這個方法只能在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]中取得。  
  
     您也可以為 <xref:System.Windows.Forms.Clipboard.SetData%2A> 方法使用預先定義的格式名稱。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.DataFormats>。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### 若要以多種格式從剪貼簿擷取資料  
  
1.  請使用 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 方法。  您必須使用這個方法，才能從 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 之前版本的剪貼簿擷取資料。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## 請參閱  
 [拖放作業和剪貼簿支援](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)   
 [如何：將資料加入至剪貼簿](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)