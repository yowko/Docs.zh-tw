---
title: "建立來源 Office Open XML 文件 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 928a3c34836464e7603c485b64c9c426913ae7b2
ms.lasthandoff: 03/13/2017


---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>建立來源 Office Open XML 文件 (Visual Basic)
這個主題顯示如何建立此教學課程中其他範例所使用的 Office Open XML WordprocessingML 文件。 如果您按照這些指示進行，您的輸出將會符合每個範例中提供的輸出。  
  
 不過，本教學課程中的範例將會使用任何有效的 WordprocessingML 文件。  
  
 若要建立本教學課程使用的文件，您必須有 Microsoft Office 2007 安裝或更新版本，或您必須具有 Microsoft Office 2003 與 Microsoft Office Compatibility Pack for Word、 Excel 和 PowerPoint 2007 檔案格式。  
  
## <a name="creating-the-wordprocessingml-document"></a>建立 WordprocessingML 文件  
  
#### <a name="to-create-the-wordprocessingml-document"></a>若要建立 WordprocessingML 文件  
  
1.  建立新的 Microsoft Word 文件。  
  
2.  將下列文字貼到新的文件中：  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  將第一行的格式設定為「標題 1」樣式。  
  
4.  選取包含 Visual Basic 程式碼的行。 第一行開頭為 `Imports` 關鍵字。 最後一行是 「 結束類別 」。 利用 Courier 字型設定這幾行的格式。 以新樣式設定格式，然後將新樣式命名為 "Code"。  
  
5.  最後，選取包含輸出的整行，然後使用 `Code` 樣式設定其格式。  
  
6.  儲存文件，然後將其命名為 SampleDoc.docx。  
  
    > [!NOTE]
    >  如果您使用 Microsoft Word 2003，請選取**Word 2007 文件**中**檔案類型**下拉式清單。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程︰ 操作 WordprocessingML 文件 (Visual Basic) 中的內容](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
