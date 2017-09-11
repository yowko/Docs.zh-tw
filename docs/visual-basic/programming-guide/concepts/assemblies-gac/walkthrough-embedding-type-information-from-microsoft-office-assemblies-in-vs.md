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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: c527941d6eae56d66cbede92ced3f66d24937354
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="5a77d-102">逐步解說︰ 將從 Microsoft Office 組件的類型資訊內嵌在 Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a77d-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="5a77d-103">如果您參考的 COM 物件的應用程式中內嵌類型資訊，您可以不需要主要 interop 組件 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="5a77d-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="5a77d-104">此外，內嵌的類型資訊可讓您達成版本獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="5a77d-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="5a77d-105">也就是您的程式可以寫入使用 COM 程式庫的多個版本的型別，而不需要特定的 PIA，每個版本。</span><span class="sxs-lookup"><span data-stu-id="5a77d-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="5a77d-106">這是與 Microsoft Office 文件庫中使用物件的應用程式的常見案例。</span><span class="sxs-lookup"><span data-stu-id="5a77d-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="5a77d-107">內嵌類型資訊，可讓相同組建的程式以使用不同版本的 Microsoft Office，而不需要重新部署的程式或每個版本的 Microsoft Office PIA 的不同電腦上。</span><span class="sxs-lookup"><span data-stu-id="5a77d-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="5a77d-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="5a77d-108">Prerequisites</span></span>  
 <span data-ttu-id="5a77d-109">本逐步解說需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="5a77d-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="5a77d-110">會安裝 Visual Studio 和 Microsoft Excel 的電腦。</span><span class="sxs-lookup"><span data-stu-id="5a77d-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="5a77d-111">第二部電腦，會安裝.NET Framework 4 或更新版本和不同的 excel 版本。</span><span class="sxs-lookup"><span data-stu-id="5a77d-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <span data-ttu-id="5a77d-112"><a name="BKMK_createapp"></a>若要建立使用多個版本的 Microsoft Office 應用程式</span><span class="sxs-lookup"><span data-stu-id="5a77d-112"><a name="BKMK_createapp"></a> To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="5a77d-113">啟動 Visual Studio 安裝 Excel 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5a77d-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="5a77d-114">在 [檔案] **** 功能表上，依序選擇 [新增] ****和 [專案] ****。</span><span class="sxs-lookup"><span data-stu-id="5a77d-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="5a77d-115">在**新的專案**對話方塊中，於**專案類型** 窗格中，請確定**Windows**已選取。</span><span class="sxs-lookup"><span data-stu-id="5a77d-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="5a77d-116">選取**主控台應用程式**中**範本**窗格。</span><span class="sxs-lookup"><span data-stu-id="5a77d-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="5a77d-117">在**名稱**方塊中，輸入`CreateExcelWorkbook`，然後選擇 [**確定**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5a77d-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="5a77d-118">建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="5a77d-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="5a77d-119">開啟 CreateExcelWorkbook 專案的捷徑功能表，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5a77d-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="5a77d-120">選擇**參考** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5a77d-120">Choose the **References** tab.</span></span> <span data-ttu-id="5a77d-121">選擇 [ **加入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5a77d-121">Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="5a77d-122">在**.NET**索引標籤上，選擇最新版本`Microsoft.Office.Interop.Excel`。</span><span class="sxs-lookup"><span data-stu-id="5a77d-122">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="5a77d-123">例如， **Microsoft.Office.Interop.Excel 版本為 14.0.0.0**。</span><span class="sxs-lookup"><span data-stu-id="5a77d-123">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="5a77d-124">選擇 [確定] **** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5a77d-124">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="5a77d-125">中的參考清單**CreateExcelWorkbook**專案中，選取的參考`Microsoft.Office.Interop.Excel`您在上一個步驟中加入。</span><span class="sxs-lookup"><span data-stu-id="5a77d-125">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="5a77d-126">在**屬性** 視窗中，請確定`Embed Interop Types`屬性設定為`True`。</span><span class="sxs-lookup"><span data-stu-id="5a77d-126">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a77d-127">由於內嵌 interop 類型資訊，以不同版本的 Microsoft Office 執行本逐步解說中建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5a77d-127">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="5a77d-128">如果`Embed Interop Types`屬性設定為`False`，您必須包含每個版本的應用程式會執行與 Microsoft Office PIA。</span><span class="sxs-lookup"><span data-stu-id="5a77d-128">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="5a77d-129">開啟 Module1.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="5a77d-129">Open the Module1.vb file.</span></span> <span data-ttu-id="5a77d-130">下列程式碼取代檔案中的程式碼︰</span><span class="sxs-lookup"><span data-stu-id="5a77d-130">Replace the code in the file with the following code:</span></span>  
  
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
  
8.  <span data-ttu-id="5a77d-131">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="5a77d-131">Save the project.</span></span>  
  
9. <span data-ttu-id="5a77d-132">按 CTRL + F5 以建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="5a77d-132">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="5a77d-133">確認 Excel 活頁簿已經建立的範例程式碼中指定的位置︰ C:\SampleFolder\SampleWorkbook.xls。</span><span class="sxs-lookup"><span data-stu-id="5a77d-133">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <span data-ttu-id="5a77d-134"><a name="BKMK_publishapp"></a>要發行到電腦安裝不同版本的 Microsoft Office 應用程式</span><span class="sxs-lookup"><span data-stu-id="5a77d-134"><a name="BKMK_publishapp"></a> To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="5a77d-135">開啟 Visual Studio 中的這個逐步解說所建立的專案。</span><span class="sxs-lookup"><span data-stu-id="5a77d-135">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="5a77d-136">在**建置**] 功能表上，選擇 [**發行 CreateExcelWorkbook**。</span><span class="sxs-lookup"><span data-stu-id="5a77d-136">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="5a77d-137">若要建立的應用程式可安裝版本的發行精靈的步驟。</span><span class="sxs-lookup"><span data-stu-id="5a77d-137">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="5a77d-138">如需詳細資訊，請參閱[發行精靈 （在 Visual Studio 中的 Office 程式開發）](https://msdn.microsoft.com/library/bb625071)。</span><span class="sxs-lookup"><span data-stu-id="5a77d-138">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="5a77d-139">安裝應用程式會安裝.NET Framework 4 或更新版本和不同的 excel 版本的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5a77d-139">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="5a77d-140">當安裝完成時，執行安裝的程式。</span><span class="sxs-lookup"><span data-stu-id="5a77d-140">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="5a77d-141">確認 Excel 活頁簿已經建立的範例程式碼中指定的位置︰ C:\SampleFolder\SampleWorkbook.xls。</span><span class="sxs-lookup"><span data-stu-id="5a77d-141">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a77d-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a77d-142">See Also</span></span>  
 <span data-ttu-id="5a77d-143">[逐步解說︰ 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span><span class="sxs-lookup"><span data-stu-id="5a77d-143">[Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span></span>  
<span data-ttu-id="5a77d-144"> [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)</span><span class="sxs-lookup"><span data-stu-id="5a77d-144"> [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)</span></span>

