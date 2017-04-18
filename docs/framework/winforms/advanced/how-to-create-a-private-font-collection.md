---
title: "如何：建立私用字型集合 | Microsoft Docs"
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
  - "字型, 建立私用集合"
  - "私用字型集合, 建立"
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：建立私用字型集合
<xref:System.Drawing.Text.PrivateFontCollection> 類別繼承自 <xref:System.Drawing.Text.FontCollection> 抽象基底類別。  您可以使用 <xref:System.Drawing.Text.PrivateFontCollection> 物件來保留一組專供應用程式使用的字型。  私用字型集合可包括已安裝的系統字型，以及尚未安裝到電腦上的字型。  若要將字型檔加入至私用字型集合，請呼叫 <xref:System.Drawing.Text.PrivateFontCollection> 物件的 <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> 方法。  
  
 <xref:System.Drawing.Text.PrivateFontCollection> 物件的 <xref:System.Drawing.Text.FontCollection.Families%2A> 屬性包含 <xref:System.Drawing.FontFamily> 物件陣列。  
  
 私用字型集合中的字型家族數目不一定和已加入集合中的字型檔案數目相同。  例如，假設您將 ArialBd.tff、Times.tff 和 TimesBd.tff 檔案加入集合中。  雖然集合中有三個檔案，但是只有兩個家族，因為 Times.tff 和 TimesBd.tff 屬於同一個家族。  
  
## 範例  
 下列範例將以下三個字型檔加入至 <xref:System.Drawing.Text.PrivateFontCollection> 物件：  
  
-   C:\\*systemroot*\\Fonts\\Arial.tff \(Arial，標準\)  
  
-   C:\\*systemroot*\\Fonts\\CourBI.tff \(Courier New，粗斜體\)  
  
-   C:\\*systemroot*\\Fonts\\TimesBd.tff \(Times New Roman，粗體\)  
  
 此程式碼會從 <xref:System.Drawing.Text.PrivateFontCollection> 物件的 <xref:System.Drawing.Text.FontCollection.Families%2A> 屬性中擷取 <xref:System.Drawing.FontFamily> 物件陣列。  
  
 程式碼會對集合中的每一個 <xref:System.Drawing.FontFamily> 物件，呼叫 <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> 方法，以決定是否可使用不同的樣式 \(標準、粗體、斜體、粗斜體、底線和刪除線\)。  傳遞至 <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> 方法的引數是 <xref:System.Drawing.FontStyle> 列舉型別的成員。  
  
 如果指定的家族\/樣式組合可供使用，便會使用該家族和樣式來建構 <xref:System.Drawing.Font> 物件。  傳遞至 <xref:System.Drawing.Font.%23ctor%2A> 建構函式的第一個引數是字型家族名稱 \(而非 <xref:System.Drawing.Font.%23ctor%2A> 建構函式其他變化案例中的 <xref:System.Drawing.FontFamily> 物件\)。  <xref:System.Drawing.Font> 物件建構完成後，會將它傳遞至 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawString%2A> 方法，將家族名稱和樣式名稱一起顯示出來。  
  
 下列程式碼的輸出與下圖中所顯示的輸出類似。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")  
  
 Arial.tff \(已在下列程式碼範例中加入至私用字型集合\) 是 Arial 標準樣式的字型檔。  但是請注意，程式輸出除了會顯示 Arial 字型家族的標準樣式之外，還會顯示其他幾種可用的樣式。  這是因為 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可以從標準樣式模擬粗體、斜體和粗斜體等樣式。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 也可根據標準樣式產生底線和刪除線。  
  
 同樣地，[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可根據粗體樣式或斜體樣式來模擬粗斜體樣式。  因此，即使 TimesBd.tff \(Times New Roman Bold\) 是集合中唯一的 Times 檔案，但是程式輸出仍然會顯示 Times 家族可使用粗斜體樣式。  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## 編譯程式碼  
 前述範例是專為與 Windows Form 搭配使用而設計的，而且它需要有 <xref:System.Windows.Forms.PaintEventArgs> `e` \(這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 <xref:System.Drawing.Text.PrivateFontCollection>   
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)