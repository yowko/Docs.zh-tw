---
title: 建立來源 Office Open XML 檔-LINQ to XML
description: 瞭解如何建立本教學課程中其他範例所使用的 Office Open XML WordprocessingML 檔。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: b3401d7309879661dcfc7062418ee75430dccf35
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552083"
---
# <a name="create-the-source-office-open-xml-document-linq-to-xml"></a>建立來源 Office Open XML 檔 (LINQ to XML) 

本文說明如何建立本教學課程中其他範例所使用的 Office Open XML WordprocessingML 檔。 如果您按照這些指示進行，您的輸出將會符合每個範例中提供的輸出。

不過，本教學課程中的範例將會使用任何有效的 WordprocessingML 文件。

若要建立本教學課程使用的文件，您必須已經安裝 Microsoft Office 2007 或更新版本；或者，您必須安裝 Microsoft Office 2003 與適用於 Word、Excel 和 PowerPoint 2007 檔案格式的 Microsoft Office 相容性套件。

## <a name="create-the-wordprocessingml-document"></a>建立 WordprocessingML 檔

使用下列步驟來建立 WordprocessingML 檔：

1. 建立新的 Microsoft Word 文件。
1. 將下列文字貼到新的檔中。
   1. 若為 c #，請使用下列文字：

         ```text
         Parsing WordprocessingML with LINQ to XML

         The following example prints to the console.

         using System;

            class Program {
               public static void Main(string[] args) {
               Console.WriteLine("Hello World");
            }
         }

         This example produces the following output:

         Hello World
         ```

   1. 針對 Visual Basic，請使用下列文字：

      ```text
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

1. 將第一行的格式設定為「標題 1」樣式。
1. 若為 c #，請選取包含 c # 程式碼的程式列。 第一行開頭為 `using` 關鍵字。 最後一行是最後一個右邊的大括號。 利用 Courier 字型設定這幾行的格式。 以新樣式設定格式，然後將新樣式命名為 "Code"。
1. 針對 Visual Basic，請選取包含 Visual Basic 代碼的行。 第一行開頭為 `Imports` 關鍵字。 最後一行是「End Class」。 利用 Courier 字型設定這幾行的格式。 以新樣式設定格式，然後將新樣式命名為 "Code"。
1. 最後，選取包含輸出的整行，然後使用 `Code` 樣式設定其格式。
1. 儲存文件，然後將其命名為 SampleDoc.docx。

> [!NOTE]
> 如果您使用的是 Microsoft Word 2003，請在 [檔**類型**] 下拉式清單中選取 [ **Word 2007 檔**]。

## <a name="see-also"></a>另請參閱

- [教學課程：操作 WordprocessingML 檔中的內容](xml-shape-wordprocessingml-documents.md)
