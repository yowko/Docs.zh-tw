---
title: "逐步解說︰ 將從 Microsoft Office 組件的類型資訊內嵌在 Visual Studio (Visual Basic) |Microsoft 文件"
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
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4347ba0e740419b53a1aa662c43933dead107e9c
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>逐步解說︰ 將從 Microsoft Office 組件的類型資訊內嵌在 Visual Studio (Visual Basic)
如果您參考的 COM 物件的應用程式中內嵌類型資訊，您可以不需要主要 interop 組件 (PIA)。 此外，內嵌的類型資訊可讓您達成版本獨立應用程式。 也就是您的程式可以寫入使用 COM 程式庫的多個版本的型別，而不需要特定的 PIA，每個版本。 這是與 Microsoft Office 文件庫中使用物件的應用程式的常見案例。 內嵌類型資訊，可讓相同組建的程式以使用不同版本的 Microsoft Office，而不需要重新部署的程式或每個版本的 Microsoft Office PIA 的不同電腦上。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 本逐步解說需要下列項目：  
  
-   會安裝 Visual Studio 和 Microsoft Excel 的電腦。  
  
-   第二部電腦，會安裝.NET Framework 4 或更新版本和不同的 excel 版本。  
  
##  <a name="BKMK_createapp"></a>若要建立使用多個版本的 Microsoft Office 應用程式  
  
1.  啟動 Visual Studio 安裝 Excel 的電腦上。  
  
2.  在 [檔案] **** 功能表上，依序選擇 [新增] ****和 [專案] ****。  
  
3.  在**新的專案**對話方塊中，於**專案類型** 窗格中，請確定**Windows**已選取。 選取**主控台應用程式**中**範本**窗格。 在**名稱**方塊中，輸入`CreateExcelWorkbook`，然後選擇 [**確定**] 按鈕。 建立新的專案。  
  
4.  開啟 CreateExcelWorkbook 專案的捷徑功能表，然後選擇**屬性**。 選擇**參考** 索引標籤。 選擇 [ **加入** ] 按鈕。  
  
5.  在**.NET**索引標籤上，選擇最新版本`Microsoft.Office.Interop.Excel`。 例如， **Microsoft.Office.Interop.Excel 版本為 14.0.0.0**。 選擇 [確定] **** 按鈕。  
  
6.  中的參考清單**CreateExcelWorkbook**專案中，選取的參考`Microsoft.Office.Interop.Excel`您在上一個步驟中加入。 在**屬性** 視窗中，請確定`Embed Interop Types`屬性設定為`True`。  
  
    > [!NOTE]
    >  由於內嵌 interop 類型資訊，以不同版本的 Microsoft Office 執行本逐步解說中建立的應用程式。 如果`Embed Interop Types`屬性設定為`False`，您必須包含每個版本的應用程式會執行與 Microsoft Office PIA。  
  
7.  開啟 Module1.vb 檔案。 下列程式碼取代檔案中的程式碼︰  
  
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
  
9. 按 CTRL + F5 以建置並執行專案。 確認 Excel 活頁簿已經建立的範例程式碼中指定的位置︰ C:\SampleFolder\SampleWorkbook.xls。  
  
##  <a name="BKMK_publishapp"></a>要發行到電腦安裝不同版本的 Microsoft Office 應用程式  
  
1.  開啟 Visual Studio 中的這個逐步解說所建立的專案。  
  
2.  在**建置**] 功能表上，選擇 [**發行 CreateExcelWorkbook**。 若要建立的應用程式可安裝版本的發行精靈的步驟。 如需詳細資訊，請參閱[發行精靈 （在 Visual Studio 中的 Office 程式開發）](https://msdn.microsoft.com/library/bb625071)。  
  
3.  安裝應用程式會安裝.NET Framework 4 或更新版本和不同的 excel 版本的電腦上。  
  
4.  當安裝完成時，執行安裝的程式。  
  
5.  確認 Excel 活頁簿已經建立的範例程式碼中指定的位置︰ C:\SampleFolder\SampleWorkbook.xls。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)   
 [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)

