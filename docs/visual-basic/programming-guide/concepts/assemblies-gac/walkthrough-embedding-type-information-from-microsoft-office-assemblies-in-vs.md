---
title: 逐步解說： 在 Visual Studio (Visual Basic) 中內嵌來自 Microsoft Office 組件的類型資訊
ms.date: 07/20/2015
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
ms.openlocfilehash: bc8f7585964bdd60bac5d5a466f6276fab288c78
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668206"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>逐步解說： 在 Visual Studio (Visual Basic) 中內嵌來自 Microsoft Office 組件的類型資訊
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
  
4.  開啟 CreateExcelWorkbook 專案的捷徑功能表，然後選擇**屬性**。 選擇**參考** 索引標籤。選擇  **加入**  按鈕。  
  
5.  在 [.NET] 索引標籤上，選擇最新版本的 `Microsoft.Office.Interop.Excel`。 例如，**Microsoft.Office.Interop.Excel 14.0.0.0**。 選擇 [確定]  按鈕。  
  
6.  在 **CreateExcelWorkbook** 專案的參考清單中，選取上一個步驟所加入的 `Microsoft.Office.Interop.Excel` 參考。 在 [屬性] 視窗中，確認 `Embed Interop Types` 屬性已設為 `True`。  
  
    > [!NOTE]
    >  由於使用了內嵌的 Interop 類型資訊，因此本逐步解說所建立的應用程式可執行於不同版本的 Microsoft Office。 如果 `Embed Interop Types` 屬性設定為 `False`，您就必須將執行應用程式之每個版本 Microsoft Office 的 PIA 包含在內。  
  
7.  開啟 Module1.vb 檔案。 以下列程式碼取代檔案中的程式碼：  
  
    ```vb  
    Imports Excel = Microsoft.Office.Interop.Excel  
  
    Module Module1  
  
        Sub Main()  
            Dim values = {4, 6, 18, 2, 1, 76, 0, 3, 11}  
  
            CreateWorkbook(values, "C:\SampleFolder\SampleWorkbook.xls")  
        End Sub  
  
        Sub CreateWorkbook(ByVal values As Integer(), ByVal filePath As String)  
            Dim excelApp As Excel.Application = Nothing  
            Dim wkbk As Excel.Workbook  
            Dim sheet As Excel.Worksheet  
  
            Try  
                ' Start Excel and create a workbook and worksheet.  
                excelApp = New Excel.Application  
                wkbk = excelApp.Workbooks.Add()  
                sheet = CType(wkbk.Sheets.Add(), Excel.Worksheet)  
                sheet.Name = "Sample Worksheet"  
  
                ' Write a column of values.  
                ' In the For loop, both the row index and array index start at 1.  
                ' Therefore the value of 4 at array index 0 is not included.  
                For i = 1 To values.Length - 1  
                    sheet.Cells(i, 1) = values(i)  
                Next  
  
                ' Suppress any alerts and save the file. Create the directory   
                ' if it does not exist. Overwrite the file if it exists.  
                excelApp.DisplayAlerts = False  
                Dim folderPath = My.Computer.FileSystem.GetParentPath(filePath)  
                If Not My.Computer.FileSystem.DirectoryExists(folderPath) Then  
                    My.Computer.FileSystem.CreateDirectory(folderPath)  
                End If  
                wkbk.SaveAs(filePath)  
        Catch  
  
            Finally  
                sheet = Nothing  
                wkbk = Nothing  
  
                ' Close Excel.  
                excelApp.Quit()  
                excelApp = Nothing  
            End Try  
  
        End Sub  
    End Module  
    ```  
  
8.  儲存專案。  
  
9. 按 CTRL+F5 建置並執行專案。 確認範例程式碼中指定的位置 (C:\SampleFolder\SampleWorkbook.xls) 已建立 Excel 活頁簿。  
  
##  <a name="BKMK_publishapp"></a> 若要將應用程式發行到安裝不同版本的 Microsoft Office 電腦  
  
1.  在 Visual Studio 中，開啟本逐步解說所建立的專案。  
  
2.  在 [建置] 功能表上，選擇 [發行 CreateExcelWorkbook]。 遵循 [發行精靈] 的步驟，建立應用程式的可安裝版本。 如需詳細資訊，請參閱[發行精靈 (Visual Studio 中的 Office 程式開發)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio)。  
  
3.  在已安裝 .NET Framework 4 或更新版本和不同版本 Excel 的電腦上，安裝應用程式。  
  
4.  當安裝完成時，執行已安裝的程式。  
  
5.  確認範例程式碼中指定的位置 (C:\SampleFolder\SampleWorkbook.xls) 已建立 Excel 活頁簿。  
  
## <a name="see-also"></a>另請參閱

- [逐步解說： 在 Visual Studio (Visual Basic) 中內嵌來自 Managed 組件的型別](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
- [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
