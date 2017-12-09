---
title: "逐步解說： 將從 Microsoft Office 組件的類型資訊內嵌在 Visual Studio (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26e6fee5147e8477c64f7eaf0dc2aeb928c13e15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="c9448-102">逐步解說： 將從 Microsoft Office 組件的類型資訊內嵌在 Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9448-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="c9448-103">如果您在參考 COM 物件的應用程式中內嵌類型資訊，就不必使用主要 Interop 組件 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="c9448-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="c9448-104">此外，內嵌的類型資訊可讓您確保應用程式的版本獨立。</span><span class="sxs-lookup"><span data-stu-id="c9448-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="c9448-105">也就是說，您可以撰寫程式來使用 COM 程式庫多個版本的類型，而不需每個版本使用特定的 PIA。</span><span class="sxs-lookup"><span data-stu-id="c9448-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="c9448-106">當應用程式使用來自 Microsoft Office 程式庫的物件時，這是十分常見的案例。</span><span class="sxs-lookup"><span data-stu-id="c9448-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="c9448-107">當您內嵌類型資訊時，可讓相同組建的程式在個別電腦上使用不同版本的 Microsoft Office，而不需要針對每個版本的 Microsoft Office 重新部署程式或 PIA。</span><span class="sxs-lookup"><span data-stu-id="c9448-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="c9448-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="c9448-108">Prerequisites</span></span>  
 <span data-ttu-id="c9448-109">本逐步解說需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="c9448-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="c9448-110">已安裝 Visual Studio 和 Microsoft Excel 的電腦。</span><span class="sxs-lookup"><span data-stu-id="c9448-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="c9448-111">已安裝 .NET Framework 4 或更新版本和不同版本 Excel 的第二台電腦。</span><span class="sxs-lookup"><span data-stu-id="c9448-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="c9448-112">若要建立應用程式以使用多個版本的 Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="c9448-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="c9448-113">在安裝 Excel 的電腦上啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="c9448-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="c9448-114">在 [檔案]  功能表上，依序選擇 [新增] 和 [專案] 。</span><span class="sxs-lookup"><span data-stu-id="c9448-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="c9448-115">在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="c9448-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="c9448-116">選取 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="c9448-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="c9448-117">在 [名稱] 文字方塊中，輸入 `CreateExcelWorkbook`，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9448-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="c9448-118">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="c9448-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="c9448-119">開啟 CreateExcelWorkbook 專案的捷徑功能表，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c9448-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="c9448-120">選擇**參考** 索引標籤。選擇  **加入**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9448-120">Choose the **References** tab. Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="c9448-121">在 [.NET] 索引標籤上，選擇最新版本的 `Microsoft.Office.Interop.Excel`。</span><span class="sxs-lookup"><span data-stu-id="c9448-121">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="c9448-122">例如，**Microsoft.Office.Interop.Excel 14.0.0.0**。</span><span class="sxs-lookup"><span data-stu-id="c9448-122">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="c9448-123">選擇 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9448-123">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="c9448-124">在 **CreateExcelWorkbook** 專案的參考清單中，選取上一個步驟所加入的 `Microsoft.Office.Interop.Excel` 參考。</span><span class="sxs-lookup"><span data-stu-id="c9448-124">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="c9448-125">在 [屬性] 視窗中，確認 `Embed Interop Types` 屬性已設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="c9448-125">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c9448-126">由於使用了內嵌的 Interop 類型資訊，因此本逐步解說所建立的應用程式可執行於不同版本的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="c9448-126">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="c9448-127">如果 `Embed Interop Types` 屬性設定為 `False`，您就必須將執行應用程式之每個版本 Microsoft Office 的 PIA 包含在內。</span><span class="sxs-lookup"><span data-stu-id="c9448-127">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="c9448-128">開啟 Module1.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="c9448-128">Open the Module1.vb file.</span></span> <span data-ttu-id="c9448-129">以下列程式碼取代檔案中的程式碼：</span><span class="sxs-lookup"><span data-stu-id="c9448-129">Replace the code in the file with the following code:</span></span>  
  
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
  
8.  <span data-ttu-id="c9448-130">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="c9448-130">Save the project.</span></span>  
  
9. <span data-ttu-id="c9448-131">按 CTRL+F5 建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="c9448-131">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="c9448-132">確認範例程式碼中指定的位置 (C:\SampleFolder\SampleWorkbook.xls) 已建立 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="c9448-132">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="c9448-133">若要將應用程式發行到安裝不同版本的 Microsoft Office 電腦</span><span class="sxs-lookup"><span data-stu-id="c9448-133">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="c9448-134">在 Visual Studio 中，開啟本逐步解說所建立的專案。</span><span class="sxs-lookup"><span data-stu-id="c9448-134">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="c9448-135">在 [建置] 功能表上，選擇 [發行 CreateExcelWorkbook]。</span><span class="sxs-lookup"><span data-stu-id="c9448-135">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="c9448-136">遵循 [發行精靈] 的步驟，建立應用程式的可安裝版本。</span><span class="sxs-lookup"><span data-stu-id="c9448-136">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="c9448-137">如需詳細資訊，請參閱[發行精靈 (Visual Studio 中的 Office 程式開發)](https://msdn.microsoft.com/library/bb625071)。</span><span class="sxs-lookup"><span data-stu-id="c9448-137">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="c9448-138">在已安裝 .NET Framework 4 或更新版本和不同版本 Excel 的電腦上，安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9448-138">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="c9448-139">當安裝完成時，執行已安裝的程式。</span><span class="sxs-lookup"><span data-stu-id="c9448-139">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="c9448-140">確認範例程式碼中指定的位置 (C:\SampleFolder\SampleWorkbook.xls) 已建立 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="c9448-140">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9448-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9448-141">See Also</span></span>  
 [<span data-ttu-id="c9448-142">逐步解說： 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型</span><span class="sxs-lookup"><span data-stu-id="c9448-142">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [<span data-ttu-id="c9448-143">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9448-143">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
