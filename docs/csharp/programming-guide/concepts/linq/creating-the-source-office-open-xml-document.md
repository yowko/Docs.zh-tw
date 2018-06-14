---
title: 建立來源 Office Open XML 文件 (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: c5884d1e34558d01be4c873c3f44222396e588ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324495"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>建立來源 Office Open XML 文件 (C#)
這個主題顯示如何建立此教學課程中其他範例所使用的 Office Open XML WordprocessingML 文件。 如果您按照這些指示進行，您的輸出將會符合每個範例中提供的輸出。  
  
 不過，本教學課程中的範例將會使用任何有效的 WordprocessingML 文件。  
  
 若要建立本教學課程使用的文件，您必須已經安裝 Microsoft Office 2007 或更新版本；或者，您必須安裝 Microsoft Office 2003 與適用於 Word、Excel 和 PowerPoint 2007 檔案格式的 Microsoft Office 相容性套件。  
  
## <a name="creating-the-wordprocessingml-document"></a>建立 WordprocessingML 文件  
  
#### <a name="to-create-the-wordprocessingml-document"></a>若要建立 WordprocessingML 文件  
  
1.  建立新的 Microsoft Word 文件。  
  
2.  將下列文字貼到新的文件中：  
  
    ```  
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
  
3.  將第一行的格式設定為「標題 1」樣式。  
  
4.  選取包含 C# 程式碼的行。 第一行開頭為 `using` 關鍵字。 最後一行是最後一個右邊的大括號。 利用 Courier 字型設定這幾行的格式。 以新樣式設定格式，然後將新樣式命名為 "Code"。  
  
5.  最後，選取包含輸出的整行，然後使用 `Code` 樣式設定其格式。  
  
6.  儲存文件，然後將其命名為 SampleDoc.docx。  
  
    > [!NOTE]
    >  如果您要使用 Microsoft Word 2003，在 [存檔類型] 下拉式清單中選取 [Word 2007 文件]。  
  
## <a name="see-also"></a>請參閱  
 [教學課程：管理 WordprocessingML 文件中的內容 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
