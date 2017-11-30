---
title: "逐步解說：在 Visual Studio 中內嵌來自 Microsoft Office 組件的型別資訊 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 45ec4521da08a9a1f4bdc3b433d3f8d765960526
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a>逐步解說：在 Visual Studio 中內嵌來自 Microsoft Office 組件的型別資訊 (C#)
如果您在參考 COM 物件的應用程式中內嵌類型資訊，就不必使用主要 Interop 組件 (PIA)。 此外，內嵌的類型資訊可讓您確保應用程式的版本獨立。 也就是說，您可以撰寫程式來使用 COM 程式庫多個版本的類型，而不需每個版本使用特定的 PIA。 當應用程式使用來自 Microsoft Office 程式庫的物件時，這是十分常見的案例。 當您內嵌類型資訊時，可讓相同組建的程式在個別電腦上使用不同版本的 Microsoft Office，而不需要針對每個版本的 Microsoft Office 重新部署程式或 PIA。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 本逐步解說需要下列項目：  
  
-   已安裝 Visual Studio 和 Microsoft Excel 的電腦。  
  
-   已安裝 .NET Framework 4 或更新版本和不同版本 Excel 的第二台電腦。  
  
##  <a name="BKMK_createapp"></a> 若要建立應用程式以使用多個版本的 Microsoft Office  
  
1.  在安裝 Excel 的電腦上啟動 Visual Studio。  
  
2.  在 [檔案]  功能表上，依序選擇 [新增] 和 [專案] 。  
  
3.  在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。 選取 [範本] 窗格中的 [主控台應用程式]。 在 [名稱] 文字方塊中，輸入 `CreateExcelWorkbook`，然後選擇 [確定] 按鈕。 隨即會建立新專案。  
  
4.  在方案總管中，開啟 [參考] 的捷徑功能表，然後選擇 [加入參考]。  
  
5.  在 [.NET] 索引標籤上，選擇最新版本的 `Microsoft.Office.Interop.Excel`。 例如，**Microsoft.Office.Interop.Excel 14.0.0.0**。 選擇 [確定]  按鈕。  
  
6.  在 **CreateExcelWorkbook** 專案的參考清單中，選取上一個步驟所加入的 `Microsoft.Office.Interop.Excel` 參考。 在 [屬性] 視窗中，確認 `Embed Interop Types` 屬性已設為 `True`。  
  
    > [!NOTE]
    >  由於使用了內嵌的 Interop 類型資訊，因此本逐步解說所建立的應用程式可執行於不同版本的 Microsoft Office。 如果 `Embed Interop Types` 屬性設定為 `False`，您就必須將執行應用程式之每個版本 Microsoft Office 的 PIA 包含在內。  
  
7.  開啟 **Program.cs** 檔案。 以下列程式碼取代檔案中的程式碼：  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.IO;  
    using Excel = Microsoft.Office.Interop.Excel;  
  
    namespace CreateExcelWorkbook  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                int[] values = {4, 6, 18, 2, 1, 76, 0, 3, 11};  
  
                CreateWorkbook(values, @"C:\SampleFolder\SampleWorkbook.xls");  
            }  
  
            static void CreateWorkbook(int[] values, string filePath)  
            {  
                Excel.Application excelApp = null;  
                Excel.Workbook wkbk;  
                Excel.Worksheet sheet;  
  
                try  
                {  
                        // Start Excel and create a workbook and worksheet.  
                        excelApp = new Excel.Application();  
                        wkbk = excelApp.Workbooks.Add();  
                        sheet = wkbk.Sheets.Add() as Excel.Worksheet;  
                        sheet.Name = "Sample Worksheet";  
  
                        // Write a column of values.  
                        // In the For loop, both the row index and array index start at 1.  
                        // Therefore the value of 4 at array index 0 is not included.  
                        for (int i = 1; i < values.Length; i++)  
                        {  
                            sheet.Cells[i, 1] = values[i];  
                        }  
  
                        // Suppress any alerts and save the file. Create the directory   
                        // if it does not exist. Overwrite the file if it exists.  
                        excelApp.DisplayAlerts = false;  
                        string folderPath = Path.GetDirectoryName(filePath);  
                        if (!Directory.Exists(folderPath))  
                        {  
                            Directory.CreateDirectory(folderPath);  
                        }  
                        wkbk.SaveAs(filePath);  
                }  
                catch  
                {  
                }  
                finally  
                {  
                    sheet = null;  
                    wkbk = null;  
  
                    // Close Excel.  
                    excelApp.Quit();  
                    excelApp = null;  
                }  
            }  
        }  
    }  
    ```  
  
8.  儲存專案。  
  
9. 按 CTRL+F5 建置並執行專案。 確認範例程式碼中指定的位置 (C:\SampleFolder\SampleWorkbook.xls) 已建立 Excel 活頁簿。  
  
##  <a name="BKMK_publishapp"></a> 若要將應用程式發行到安裝不同版本的 Microsoft Office 電腦  
  
1.  在 Visual Studio 中，開啟本逐步解說所建立的專案。  
  
2.  在 [建置] 功能表上，選擇 [發行 CreateExcelWorkbook]。 遵循 [發行精靈] 的步驟，建立應用程式的可安裝版本。 如需詳細資訊，請參閱[發行精靈 (Visual Studio 中的 Office 程式開發)](https://msdn.microsoft.com/library/bb625071)。  
  
3.  在已安裝 .NET Framework 4 或更新版本和不同版本 Excel 的電腦上，安裝應用程式。  
  
4.  當安裝完成時，執行已安裝的程式。  
  
5.  確認範例程式碼中指定的位置 (C:\SampleFolder\SampleWorkbook.xls) 已建立 Excel 活頁簿。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 將類型從 Managed 組件內嵌在 Visual Studio (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [/link (C# 編譯器選項)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
