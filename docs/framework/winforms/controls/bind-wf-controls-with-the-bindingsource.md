---
title: "如何：使用設計工具將 Windows Form 控制項和 BindingSource 元件加以繫結 | Microsoft Docs"
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
  - "BindingSource 元件 [Windows Form], 繫結控制項"
  - "控制項 [Windows Form], 繫結"
  - "資料繫結, BindingSource 元件"
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：使用設計工具將 Windows Form 控制項和 BindingSource 元件加以繫結
在加入控制項至表單且判斷應用程式的使用者介面之後，可以將控制項繫結至資料來源，如此使用者便能在執行階段變更和儲存與應用程式相關的資料。  
  
 利用 <xref:System.Windows.Forms.BindingSource> 控制項當做表單控制項和資料來源之間的橋樑，是繫結 Windows Form 中某個控制項或連續好幾個控制項的最簡易方式。  
  
 表單上的一或多個控制項可繫結至資料，在以下程序中，<xref:System.Windows.Forms.TextBox> 控制項會繫結至資料來源。  
  
 若要完成這個程序，會假設您將繫結至衍生自資料庫的資料來源。  如需建立來自其他資料存放區之資料來源的詳細資訊，請參閱[資料來源概觀](../Topic/Add%20new%20data%20sources.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段繫結控制項  
  
1.  將 <xref:System.Windows.Forms.TextBox> 控制項拖曳至表單上。  
  
2.  在 \[**屬性**\] 視窗中：  
  
    1.  展開 \[**\(DataBindings\)**\] 節點。  
  
    2.  按一下 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性旁的箭號。  
  
         \[**資料來源** UI 介面型別編輯器\] 隨即開啟。  
  
         如果之前已為專案或表單設定了資料來源，那麼此資料來源將會出現。  
  
3.  按一下 \[**加入專案資料來源**\] 以連接至資料並建立資料來源。  
  
4.  在 \[**資料來源組態精靈**\] 歡迎畫面中按 \[**下一步**\]。  
  
5.  在 \[**選擇資料來源類型**\] 頁面上選取 \[**資料庫**\]。  
  
6.  在 \[**選擇資料連接**\] 頁面上，從可用連接清單中選取資料連接。  如果沒有想要的資料連接，請選取 \[**新增連接**\] 以建立新的資料連接。  
  
7.  選取 \[**是，將連接儲存**\]，即可將連接字串儲存在應用程式組態檔中。  
  
8.  選取要用於應用程式的資料庫物件。  在這種情況下，請選取資料表中想要 <xref:System.Windows.Forms.TextBox> 顯示的欄位。  
  
9. 需要時，請取代預設的資料集名稱。  
  
10. 按一下 \[**完成**\]。  
  
11. 在 \[**屬性**\] 視窗中，再按一下 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性旁的箭頭。  在 \[**資料來源** UI 介面型別編輯器\] 中，選取要將 <xref:System.Windows.Forms.TextBox> 繫結至的欄位名稱。  
  
     \[**資料來源** UI 介面型別編輯器\] 關閉，資料設定完畢，該資料連接的特定 <xref:System.Windows.Forms.BindingSource> 和資料表配接器也會加入至表單。  
  
## 請參閱  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.BindingNavigator>   
 [資料來源概觀](../Topic/Add%20new%20data%20sources.md)   
 [資料來源視窗](../Topic/Data%20Sources%20Window.md)