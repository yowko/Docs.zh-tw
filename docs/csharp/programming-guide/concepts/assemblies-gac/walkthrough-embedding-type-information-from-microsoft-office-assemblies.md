---
title: "逐步解說：在 Visual Studio 中內嵌來自 Microsoft Office 組件的型別資訊 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a9a901403f34f33639a3eb5c919c337fec594dfd
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a><span data-ttu-id="742ee-102">逐步解說：在 Visual Studio 中內嵌來自 Microsoft Office 組件的型別資訊 (C#)</span><span class="sxs-lookup"><span data-stu-id="742ee-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="742ee-103">如果您在參考 COM 物件的應用程式中內嵌類型資訊，就不必使用主要 Interop 組件 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="742ee-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="742ee-104">此外，內嵌的類型資訊可讓您確保應用程式的版本獨立。</span><span class="sxs-lookup"><span data-stu-id="742ee-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="742ee-105">也就是說，您可以撰寫程式來使用 COM 程式庫多個版本的類型，而不需每個版本使用特定的 PIA。</span><span class="sxs-lookup"><span data-stu-id="742ee-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="742ee-106">當應用程式使用來自 Microsoft Office 程式庫的物件時，這是十分常見的案例。</span><span class="sxs-lookup"><span data-stu-id="742ee-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="742ee-107">當您內嵌類型資訊時，可讓相同組建的程式在個別電腦上使用不同版本的 Microsoft Office，而不需要針對每個版本的 Microsoft Office 重新部署程式或 PIA。</span><span class="sxs-lookup"><span data-stu-id="742ee-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="742ee-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="742ee-108">Prerequisites</span></span>  
 <span data-ttu-id="742ee-109">本逐步解說需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="742ee-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="742ee-110">已安裝 Visual Studio 和 Microsoft Excel 的電腦。</span><span class="sxs-lookup"><span data-stu-id="742ee-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="742ee-111">已安裝 .NET Framework 4 或更新版本和不同版本 Excel 的第二台電腦。</span><span class="sxs-lookup"><span data-stu-id="742ee-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <span data-ttu-id="742ee-112"><a name="BKMK_createapp"></a> 若要建立應用程式以使用多個版本的 Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="742ee-112"><a name="BKMK_createapp"></a> To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="742ee-113">在安裝 Excel 的電腦上啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="742ee-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="742ee-114">在 [檔案]  功能表上，依序選擇 [新增] 和 [專案] 。</span><span class="sxs-lookup"><span data-stu-id="742ee-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="742ee-115">在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="742ee-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="742ee-116">選取 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="742ee-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="742ee-117">在 [名稱] 文字方塊中，輸入 `CreateExcelWorkbook`，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="742ee-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="742ee-118">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="742ee-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="742ee-119">在方案總管中，開啟 [參考] 的捷徑功能表，然後選擇 [加入參考]。</span><span class="sxs-lookup"><span data-stu-id="742ee-119">In **Solution Explorer**, open the shortcut menu for the **References** folder and then choose **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="742ee-120">在 [.NET] 索引標籤上，選擇最新版本的 `Microsoft.Office.Interop.Excel`。</span><span class="sxs-lookup"><span data-stu-id="742ee-120">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="742ee-121">例如，**Microsoft.Office.Interop.Excel 14.0.0.0**。</span><span class="sxs-lookup"><span data-stu-id="742ee-121">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="742ee-122">選擇 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="742ee-122">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="742ee-123">在 **CreateExcelWorkbook** 專案的參考清單中，選取上一個步驟所加入的 `Microsoft.Office.Interop.Excel` 參考。</span><span class="sxs-lookup"><span data-stu-id="742ee-123">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="742ee-124">在 [屬性] 視窗中，確認 `Embed Interop Types` 屬性已設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="742ee-124">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="742ee-125">由於使用了內嵌的 Interop 類型資訊，因此本逐步解說所建立的應用程式可執行於不同版本的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="742ee-125">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="742ee-126">如果 `Embed Interop Types` 屬性設定為 `False`，您就必須將執行應用程式之每個版本 Microsoft Office 的 PIA 包含在內。</span><span class="sxs-lookup"><span data-stu-id="742ee-126">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="742ee-127">開啟 **Program.cs** 檔案。</span><span class="sxs-lookup"><span data-stu-id="742ee-127">Open the **Program.cs** file.</span></span> <span data-ttu-id="742ee-128">以下列程式碼取代檔案中的程式碼：</span><span class="sxs-lookup"><span data-stu-id="742ee-128">Replace the code in the file with the following code:</span></span>  
  
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
  
8.  <span data-ttu-id="742ee-129">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="742ee-129">Save the project.</span></span>  
  
9. <span data-ttu-id="742ee-130">按 CTRL+F5 建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="742ee-130">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="742ee-131">確認範例程式碼中指定的位置 (C:\SampleFolder\SampleWorkbook.xls) 已建立 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="742ee-131">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <span data-ttu-id="742ee-132"><a name="BKMK_publishapp"></a> 若要將應用程式發行到安裝不同版本的 Microsoft Office 電腦</span><span class="sxs-lookup"><span data-stu-id="742ee-132"><a name="BKMK_publishapp"></a> To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="742ee-133">在 Visual Studio 中，開啟本逐步解說所建立的專案。</span><span class="sxs-lookup"><span data-stu-id="742ee-133">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="742ee-134">在 [建置] 功能表上，選擇 [發行 CreateExcelWorkbook]。</span><span class="sxs-lookup"><span data-stu-id="742ee-134">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="742ee-135">遵循 [發行精靈] 的步驟，建立應用程式的可安裝版本。</span><span class="sxs-lookup"><span data-stu-id="742ee-135">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="742ee-136">如需詳細資訊，請參閱[發行精靈 (Visual Studio 中的 Office 程式開發)](https://msdn.microsoft.com/library/bb625071)。</span><span class="sxs-lookup"><span data-stu-id="742ee-136">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="742ee-137">在已安裝 .NET Framework 4 或更新版本和不同版本 Excel 的電腦上，安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="742ee-137">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="742ee-138">當安裝完成時，執行已安裝的程式。</span><span class="sxs-lookup"><span data-stu-id="742ee-138">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="742ee-139">確認範例程式碼中指定的位置 (C:\SampleFolder\SampleWorkbook.xls) 已建立 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="742ee-139">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="742ee-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="742ee-140">See Also</span></span>  
 <span data-ttu-id="742ee-141">[逐步解說：在 Visual Studio 中內嵌來自 Managed 組件的型別 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="742ee-141">[Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) </span></span>  
 [<span data-ttu-id="742ee-142">/link (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="742ee-142">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)

