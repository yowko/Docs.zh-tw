---
title: "How to: Enable XML IntelliSense in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML IntelliSense [Visual Basic]"
  - "XML [Visual Basic], IntelliSense"
  - "IntelliSense [Visual Basic], XML"
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# How to: Enable XML IntelliSense in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Visual Basic 中的 XML IntelliSense，可提供 XML 結構描述中所定義項目的文字自動完成功能。  若要啟用 Visual Basic 中的 XML IntelliSense，您必須執行下列動作：  
  
1.  針對您的應用程式要讀取或寫入的 XML 檔案，取得一個或多個相關的 XML 結構描述 \(XSD\) 檔案。  
  
2.  在專案中納入 XML 結構描述檔案。  
  
3.  將一個或多個目標命名空間匯入至程式碼檔案或專案。  目標命名空間是由 XSD 結構描述的 `targetNamespace` 或 `tns` 屬性 \(Attribute\) 來識別。  
  
     若要匯入目標命名空間，請使用 `Imports` 陳述式 \(Statement\)，或者使用 \[專案設計工具\] 中的 \[**參考**\] 頁面為專案中的所有程式碼檔案加入命名空間。  
  
 如需 Visual Basic 中 XML IntelliSense 功能的詳細資訊，請參閱 [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)。  如需匯入 XML 命名空間的詳細資訊，請參閱 [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) 或[專案設計工具，參考頁 \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
 ![視訊的連結](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") 如需本主題的影片版本，請參閱[影片：HOW TO：在 Visual Basic 中啟用 XML IntelliSense](http://go.microsoft.com/fwlink/?LinkId=102466) \(英文\)。  如需相關示範影片，請參閱[如何啟用 XML IntelliSense 和使用 XML 命名空間？](http://go.microsoft.com/fwlink/?LinkId=143035) \(英文\)。  
  
## 啟用 Visual Basic 中的 XML IntelliSense  
 如果您有 XML 檔案但是沒有其 XSD 結構描述檔案，在 SP1 中，可以使用 \[XML To Schema 精靈\] 建立 XSD 結構描述檔案。  此外，您也可以使用 Visual Studio \[XML 編輯器\] 中的結構描述推斷。  
  
#### 若要使用 XML To Schema 精靈 \(需要有 SP1\) 建立 XML 檔案的 XSD 結構描述檔案  
  
1.  在您的專案中，按一下 \[**專案**\] 功能表上的 \[**加入新項目**\]。  
  
2.  從 \[**資料**\] 或 \[**一般項目**\] 範本類別項目選取 \[**XML To Schema**\] 項目樣板。  
  
3.  為推斷之結構描述集儲存所在的 XSD 檔案提供檔案名稱，然後按一下 \[**加入**\]。  
  
4.  在 \[**從 XML 文件推斷 XML 結構描述集**\] 視窗中加入一個或多個 XML 文件，以利推斷 XML 結構描述集。  
  
    -   使用檔案總管\]中，加入含有XML文件的文字檔，然後按一下\[\] **從檔案加入**。  
  
    -   若要從超文字傳輸通訊協定 \(HTTP\) 位址加入 XML 文件，請按一下 \[**從 Web 加入**\]。  
  
    -   若要將 XML 文件複製或輸入到精靈，請按一下 \[**輸入或貼上 XML**\]。  
  
5.  當您已經指定要從中推斷 XML 結構描述集的所有 XML 文件來源時，請按一下 \[**確定**\] 推斷 XML 結構描述集。  結構描述集會儲存成一個或多個 XSD 檔案，並且存放在您的專案目錄中   \(針對結構描述中的各個 XML 命名空間分別建立一個檔案\)。  
  
#### 若要使用 Visual Studio XML 編輯器中的結構描述推斷，建立 XML 檔案的 XSD 結構描述檔案  
  
1.  在 Visual Studio XML 設計工具中編輯 XML 檔案。  
  
2.  當游標位於 XML 檔案中時，\[**XML**\] 功能表隨即顯示。  按一下 \[**XML**\] 功能表上的 \[**建立結構描述**\]。  接著便會根據從 XML 檔案推斷而來的 XSD 結構描述，建立 XSD 檔案。  
  
3.  儲存 XSD 結構描述檔案。  
  
    > [!NOTE]
    >  多份應擁有相同結構描述的 XML 文件，可能會推斷出不同的 XSD 結構描述。  例如，當某個 XML 檔案中有特定項目與屬性 \(Attribute\)，但在另一個檔案中卻沒有時，或是併入的項目順序不同時，便有可能發生這種情形。  因此，使用 XSD 結構描述推斷時，應檢查所推斷出來之 XSD 結構描述的完整性與正確性。  
  
#### 若要包含 XSD 結構描述檔案  
  
-   根據預設，您在 Visual Basic 專案中看不到 XSD 檔案。  如果您的 XSD 檔案已包含在專案的資料夾中，請按一下 \[**方案總管**\] 中的 \[**顯示所有檔案**\] 按鈕。  在 \[**方案總管**\] 中找出 XSD 檔案，以滑鼠右鍵按一下檔案，然後按一下 \[**將檔案加入至專案**\]。  
  
-   如果 XSD 檔案還不是專案的一部分，請以滑鼠右鍵按一下 \[**方案總管**\] 中您要儲存 XSD 檔案的資料夾，指向 \[**加入**\]，然後按一下 \[**現有項目**\]。  找出 XSD 檔案，然後按一下 \[**加入**\]。  
  
#### 若要將 XML 命名空間匯入至程式碼檔案  
  
1.  識別 XSD 結構描述中的目標命名空間。  
  
2.  在程式碼檔案開始處，針對目標 XML 命名空間加入 `Imports` 陳述式，如下列範例所示。  
  
     [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-enable-xml-intell_1.vb)]  
  
     若要匯入 XML 命名空間做為預設命名空間，也就是套用至沒有命名空間前置字元之 XML 項目及屬性的命名空間，請加入目標預設 XML 命名空間的 `Imports` 陳述式。  不要指定命名空間前置字元。  下列是 `Imports` 陳述式的範例。  
  
     [!code-vb[VbXmlSamples#50](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-enable-xml-intell_2.vb)]  
  
#### 若要針對專案中的所有檔案匯入 XML 命名空間  
  
1.  匯入程式碼檔案的 XML 命名空間只會套用至該程式碼檔案。  若要匯入可以套用至專案中所有程式碼檔案的 XML 命名空間，請按兩下 \[**方案總管**\] 中的 \[**我的專案**\]，開啟 \[專案設計工具\]。  
  
2.  在 \[**匯入的命名空間**\] 方塊中的 \[**參考**\] 索引標籤上，以完整 XML 命名空間宣告的格式輸入目標 XML 命名空間 \(例如，`<xmlns: ns="http://sampleNamespace">`\)。  如果目標 XML 命名空間未指定命名空間前置字元，該命名空間便是專案的預設 XML 命名空間。  
  
3.  按一下 \[**加入使用者匯入**\]。  
  
## 請參閱  
 [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [專案設計工具，參考頁 \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)   
 [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)