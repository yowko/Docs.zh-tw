---
title: "如何︰ 啟用 XML IntelliSense 在 Visual Basic |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84af19189fa3fc510c8d4f8e408cbb2a393d8b8f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-enable-xml-intellisense-in-visual-basic"></a>如何：啟用 Visual Basic 中的 XML IntelliSense
在 Visual Basic 中的 XML IntelliSense 提供 XML 結構描述中定義的項目文字的完成。 若要啟用 XML IntelliSense，Visual Basic 中，您必須執行下列作業︰  
  
1.  取得 XML 結構描述 (XSD) 檔案或檔案，您的應用程式會讀取或寫入的 XML 檔案。  
  
2.  在專案中包含的 XML 結構描述檔案。  
  
3.  匯入到您的程式碼檔案或專案的目標命名空間或命名空間。 目標命名空間由`targetNamespace`或`tns`XSD 結構描述的屬性。  
  
     若要匯入目標命名空間，請使用`Imports`陳述式，或將之命名空間的所有程式碼檔案加入專案中，使用**參考**頁面的 專案設計工具。  
  
 多個功能在 Visual Basic 中的 XML IntelliSense 的詳細資訊，請參閱[Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)。 如需有關匯入 XML 命名空間的詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)或[專案設計工具 (Visual Basic)、 參考頁](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
 ![視訊連結](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")如本主題的影片版本，請參閱[影片-如何︰ 在 Visual Basic 中啟用 XML IntelliSense](http://go.microsoft.com/fwlink/?LinkId=102466)。 如需相關的影片示範，請參閱[如何啟用 XML IntelliSense 和使用 XML 命名空間？](http://go.microsoft.com/fwlink/?LinkId=143035)。  
  
## <a name="enable-xml-intellisense-in-visual-basic"></a>啟用在 Visual Basic 中的 XML IntelliSense  
 如果您有一個 XML 檔案，但它沒有 XSD 結構描述檔案，SP1 中您可以建立 XSD 結構描述檔案使用 XML 結構描述精靈。 您也可以使用結構描述推斷 Visual Studio XML 編輯器。  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-the-xml-to-schema-wizard-requires-sp1"></a>若要使用的 XML 結構描述精靈 建立 XSD 結構描述檔案的 XML 檔案 （需要 SP1）  
  
1.  在專案中，按一下 **加入新項目**上**專案**功能表。  
  
2.  選取**Xml 結構描述**項目範本，從**資料**或**一般項目**範本類別目錄。  
  
3.  提供 XSD 檔案或檔案，推斷的結構描述集合會儲存在然後按一下 檔案名稱**新增**。  
  
4.  在**推斷 XML 結構描述集從 XML 文件** 視窗中，新增一或多個 XML 文件推斷 XML 結構描述集。  
  
    -   若要新增包含使用檔案總管] 中的 XML 文件的文字檔案，請按一下 [**從檔案新增**。  
  
    -   若要新增的 HTTP 位址的 XML 文件，請按一下 **從 Web 加入**。  
  
    -   若要複製或輸入至精靈的 XML 文件的內容，請按一下 **輸入或貼上 XML**。  
  
5.  當您指定您想要推斷 XML 結構描述集，請按一下的所有 XML 文件來源**確定**來推斷 XML 結構描述設定。 結構描述集合會儲存在您的專案資料夾中一個或多個 XSD 檔案。 （如結構描述中每個 XML 命名空間，檔案會建立）。  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-schema-inference-in-the-visual-studio-xml-editor"></a>若要使用結構描述推斷 Visual Studio XML 編輯器建立 XSD 結構描述檔案的 XML 檔案  
  
1.  編輯 Visual Studio XML 設計工具中的 XML 檔案。  
  
2.  當游標位於 XML 檔案中， **XML**功能表隨即出現。 按一下  **Create Schema**上**XML**功能表。 從 XML 檔案推斷 XSD 結構描述所建立 XSD 檔案。  
  
3.  將 XSD 結構描述檔案儲存。  
  
    > [!NOTE]
    >  從多個預期會有相同的結構描述的 XML 文件，可能會推斷出不同的 XSD 結構描述。 這可能會發生在一個 XML 檔案，而不是在另一個，找到特定項目和屬性或元素，例如包含不同的順序。 當您使用 XSD 結構描述推斷時，您應該檢閱推斷的 XSD 結構描述的完整性與正確性。  
  
#### <a name="to-include-an-xsd-schema-file"></a>要包含的 XSD 結構描述檔案  
  
-   根據預設，您無法看到 Visual Basic 專案中的 XSD 檔案。 如果 XSD 檔案已包含在專案資料夾中，按一下 [**顯示所有檔案**按鈕**方案總管] 中**。 找出 XSD 檔案中的**方案總管 中**，以滑鼠右鍵按一下檔案，然後按一下**將檔案加入至專案中**。  
  
-   如果 XSD 檔案已不屬於您專案中**方案總管] 中**，以滑鼠右鍵按一下您要儲存 XSD 檔，指向的資料夾**新增**，然後按一下 [**現有項目**。 找出 XSD 檔案，然後按一下 **新增**。  
  
#### <a name="to-import-an-xml-namespace-in-a-code-file"></a>若要匯入 XML 命名空間中的程式碼檔案  
  
1.  識別從 XSD 結構描述的目標命名空間。  
  
2.  在程式碼檔案的開頭，新增`Imports`陳述式的目標 XML 命名空間，如下列範例所示。  
  
     [!code-vb[VbXMLSamples #&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]  
  
     若要匯入 XML 命名空間當做預設命名空間，也就是套用至 XML 元素和屬性，並沒有命名空間前置詞的命名空間加入`Imports`陳述式的目標預設 XML 命名空間。 請勿指定命名空間前置詞。 下列是範例`Imports`陳述式。  
  
     [!code-vb[VbXmlSamples #&50;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]  
  
#### <a name="to-import-an-xml-namespace-for-all-files-in-a-project"></a>若要匯入專案中的所有檔案的 XML 命名空間  
  
1.  XML 命名空間中的程式碼檔案匯入適用於該程式碼檔案。 要匯入適用於所有專案中的程式碼檔案的 XML 命名空間，請按兩下，[專案設計工具開啟**我的專案**中**方案總管] 中**。  
  
2.  在**參考**索引標籤的**匯入命名空間**方塊中，輸入完整的 XML 命名空間宣告的形式的目標 XML 命名空間 (例如， `<xmlns: ns="http://sampleNamespace">`)。 如果目標 XML 命名空間中沒有指定命名空間前置詞，命名空間會在專案的預設 XML 命名空間。  
  
3.  按一下 **加入使用者匯入**。  
  
## <a name="see-also"></a>另請參閱  
 [Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [專案設計工具、參考頁 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)   
 [在 Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)

