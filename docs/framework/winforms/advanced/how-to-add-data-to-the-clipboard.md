---
title: "如何：將資料加入至剪貼簿 | Microsoft Docs"
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
  - "剪貼簿, 複製資料至"
  - "資料 [Windows Form], 複製至剪貼簿"
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：將資料加入至剪貼簿
<xref:System.Windows.Forms.Clipboard> 類別提供了一些方法，可以用來與 Windows 作業系統的剪貼簿功能互動。  許多應用程式都將剪貼簿當做資料的暫時儲存機制。  例如，文書處理器在進行剪下和貼上作業時就會使用剪貼簿。  在應用程式之間傳送資料時，剪貼簿也很有用。  
  
 當您將資料加入至剪貼簿時，可以指明資料格式，以便其他可以使用該格式的應用程式能夠辨識資料。  您也可以將資料以多種不同的格式加入剪貼簿，以增加其他可能使用這些資料的應用程式數目。  
  
 剪貼簿檔案格式是一個用來辨識格式的字串，讓使用該格式的應用程式能夠擷取相關聯的資料。  <xref:System.Windows.Forms.DataFormats> 類別會提供預先定義的格式名稱，以供您使用。  您也可以使用自己的格式名稱，或是使用物件型別做為格式。  
  
 若要將資料以一或多種格式加入剪貼簿，請使用 <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> 方法。  您可以將任何物件傳遞給這個方法，但是如果要以多種格式加入資料，則必須先將資料加入至設計成可使用多種格式的單獨物件中。  一般而言，您會將資料加入 <xref:System.Windows.Forms.DataObject>，但是您可以使用實作 <xref:System.Windows.Forms.IDataObject> 介面的任何型別。  
  
 在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]中，有一些針對簡化基本剪貼簿工作而設計的新方法，您可以利用這些方法將資料直接加入至剪貼簿中。  當您使用單一常用格式 \(例如文字\) 時，請使用這些方法。  
  
> [!NOTE]
>  所有 Windows 應用程式都會共用剪貼簿。  因此，剪貼簿的內容會根據您切換至不同的應用程式而改變。  
>   
>  <xref:System.Windows.Forms.Clipboard> 類別只能用在設定為單一執行緒 Apartment \(STA\) 模式的執行緒中。  若要使用這個類別，請確定您的 `Main` 方法是以 <xref:System.STAThreadAttribute> 屬性做為標記。  
>   
>  物件必須可以序列化，才能放在剪貼簿上。  若要讓型別可以序列化，請將它以 <xref:System.SerializableAttribute> 屬性標記。  如果您將不可序列化的物件傳入剪貼簿方法，方法將會失敗，而且不會擲回例外狀況。  如需序列化的詳細資訊，請參閱<xref:System.Runtime.Serialization>。  
  
### 若要以單一常用格式將資料加入至剪貼簿  
  
1.  請使用 <xref:System.Windows.Forms.Clipboard.SetAudio%2A>、<xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>、<xref:System.Windows.Forms.Clipboard.SetImage%2A> 或 <xref:System.Windows.Forms.Clipboard.SetText%2A> 方法。  這些方法只能在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]中取得。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### 若要以自訂格式將資料加入至剪貼簿  
  
1.  請使用具有自訂格式名稱的 <xref:System.Windows.Forms.Clipboard.SetData%2A> 方法。  這個方法只能在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]中取得。  
  
     您也可以為 <xref:System.Windows.Forms.Clipboard.SetData%2A> 方法使用預先定義的格式名稱。  如需詳細資訊，請參閱 <xref:System.Windows.Forms.DataFormats>。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### 若要以多種格式將資料加入至剪貼簿  
  
1.  請使用 <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> 方法並傳遞包含資料的 <xref:System.Windows.Forms.DataObject>。  您必須使用這個方法，才能將資料加入至 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 之前版本的剪貼簿。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## 請參閱  
 [拖放作業和剪貼簿支援](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)   
 [如何：從剪貼簿擷取資料](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)