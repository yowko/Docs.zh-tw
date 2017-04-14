---
title: "如何：變更 Managed HTML 文件物件模型中的項目樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Managed HTML DOM, 變更項目上的樣式"
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：變更 Managed HTML 文件物件模型中的項目樣式
您可以利用 HTML 中的樣式來控制文件及其項目的外觀。  <xref:System.Windows.Forms.HtmlDocument> 和 <xref:System.Windows.Forms.HtmlElement> 支援 <xref:System.Windows.Forms.HtmlElement.Style%2A> 屬性，這些屬性接受以下格式的樣式字串：  
  
 `name1:value1;...;nameN:valueN;`  
  
 此處 `DIV` 的樣式字串將字型設為 Arial 並將所有文字設為粗體：  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 使用 <xref:System.Windows.Forms.HtmlElement.Style%2A> 屬性管理樣式的問題在於，這個屬性可能會使得從字串加入或移除個別樣式等作業變得難以處理。  例如，當使用者將游標置於 `DIV` 上時先前的文字要以斜體呈現，且在游標離開 `DIV` 後取消斜體設定，像是這樣的程序對您而言可能會變得太過複雜。  如果您需要以這種方式管理大量的樣式，時間會成為一大問題。  
  
 您可利用下列程序中所包含的程式碼，即可輕鬆管理 HTML 文件和項目上的樣式。  您必須知道如何執行基礎作業，例如建立新專案以及將控制項加入表單中，才能夠進行這項程序。  
  
### 若要在 Windows Form 應用程式中處理樣式變更  
  
1.  建立新的 Windows Form 專案。  
  
2.  建立新的類別檔，且副檔案必須符合您所使用的程式語言。  
  
3.  將本主題＜範例＞一節的 `StyleGenerator` 類別程式碼複製到類別檔案，並且儲存此程式碼。  
  
4.  將以下 HTML 儲存成命名為 Test.htm 的檔案。  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  將名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項加入至專案的主要表單中。  
  
6.  將下列程式碼加入至專案程式碼檔中：  
  
    > [!IMPORTANT]
    >  請確認 `webBrowser1_DocumentCompleted` 事件處理常式已設定為 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件的接聽程式。  請在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中按兩下 <xref:System.Windows.Forms.WebBrowser> 控制項並在文字編輯器中以程式設計方式設定接聽程式。  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  執行專案。  請執行第一個 `DIV` 上的游標，以觀察程式碼的效果。  
  
## 範例  
 下列程式碼範例顯示 `StyleGenerator` 類別的完整程式碼，它會剖析現有的樣式值、支援加入、變更和移除樣式，並且在完成變更要求後傳回新的樣式值。  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Forms.HtmlElement>