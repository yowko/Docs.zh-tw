---
title: 如何：變更 Managed HTML 文件物件模型中的項目樣式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e833a15e33d0baf80f0078b26758137e7908a8fd
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>如何：變更 Managed HTML 文件物件模型中的項目樣式
您可以使用 html 樣式以控制文件和其項目的外觀。 <xref:System.Windows.Forms.HtmlDocument> 和<xref:System.Windows.Forms.HtmlElement>支援<xref:System.Windows.Forms.HtmlElement.Style%2A>採用下列格式的樣式字串的屬性：  
  
 `name1:value1;...;nameN:valueN;`  
  
 以下是`DIV`與設定要以粗體顯示的 新細明體和所有文字的字型樣式字串：  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 與處理使用的樣式問題<xref:System.Windows.Forms.HtmlElement.Style%2A>屬性是，它可以證明麻煩加入和移除字串中的個別樣式設定。 例如，它就會變成複雜的程序，為您呈現上一個斜體文字，每當使用者將游標置於`DIV`，並關閉當游標離開斜體`DIV`。 如果您需要管理大量的這種方式中的樣式，時間就會成為問題。  
  
 下列程序包含程式碼可讓您輕鬆地管理 HTML 文件和項目上的樣式。 此程序需要您了解如何在 Windows Form，例如建立新的專案，以及將控制項加入表單中執行基本工作。  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a>處理 Windows Form 應用程式中的樣式變更  
  
1.  建立新的 Windows Form 專案。  
  
2.  建立新的類別檔案，結尾適用於您的程式語言的延伸模組。  
  
3.  複製`StyleGenerator`類別檔中，類別本主題的範例 > 一節中的程式碼，並儲存程式碼。  
  
4.  將下列 HTML 儲存到名為 Test.htm 的檔案。  
  
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
  
5.  新增<xref:System.Windows.Forms.WebBrowser>控制項，名為`webBrowser1`加入主要表單的專案。  
  
6.  將下列程式碼加入至您的專案程式碼檔案。  
  
    > [!IMPORTANT]
    >  請確認`webBrowser1_DocumentCompleted`事件處理常式設定為接聽程式<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件。 在 Visual Studio 中，按兩下<xref:System.Windows.Forms.WebBrowser>控制; 請在文字編輯器中，接聽程式以程式設計方式設定。  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  執行專案。 執行您的資料指標在第一個`DIV`觀察程式碼的效果。  
  
## <a name="example"></a>範例  
 下列程式碼範例顯示的完整程式碼`StyleGenerator`類別，它會剖析現有的樣式值，支援加入、 變更，並移除樣式，並傳回新的樣式值，變更要求。  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.HtmlElement>
