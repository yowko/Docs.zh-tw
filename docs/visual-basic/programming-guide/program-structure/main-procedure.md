---
title: "Visual Basic 中的 Main 程序"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6de98ad4e470cd0becaf25f5a9a00c8095e44b15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="32d32-102">Visual Basic 中的 Main 程序</span><span class="sxs-lookup"><span data-stu-id="32d32-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="32d32-103">每個 Visual Basic 應用程式必須包含呼叫的程序`Main`。</span><span class="sxs-lookup"><span data-stu-id="32d32-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="32d32-104">起始點和應用程式的整體控制，就會作為此程序。</span><span class="sxs-lookup"><span data-stu-id="32d32-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="32d32-105">.NET Framework 會呼叫您`Main`程序時已載入您的應用程式已準備好將控制權傳給它。</span><span class="sxs-lookup"><span data-stu-id="32d32-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="32d32-106">除非您要建立 Windows Forms 應用程式，您必須撰寫`Main`上執行自己的應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="32d32-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="32d32-107">`Main`包含會先執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="32d32-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="32d32-108">在`Main`，您可以決定要在程式啟動時，第一次載入的表單中，找出您的應用程式的複本是否已執行系統上、 應用程式建立一組變數或開啟應用程式需要的資料庫。</span><span class="sxs-lookup"><span data-stu-id="32d32-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="32d32-109">主要程序的需求</span><span class="sxs-lookup"><span data-stu-id="32d32-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="32d32-110">在執行它自己 （通常具有副檔名.exe) 檔案必須包含`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="32d32-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="32d32-111">不執行於它自己的程式庫 （例如使用副檔名.dll)，而且不需要`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="32d32-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="32d32-112">您可以建立不同類型的專案的需求如下所示：</span><span class="sxs-lookup"><span data-stu-id="32d32-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="32d32-113">主控台應用程式上執行其本身，以及您必須提供至少一個`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="32d32-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="32d32-114">.</span><span class="sxs-lookup"><span data-stu-id="32d32-114">.</span></span>  
  
-   <span data-ttu-id="32d32-115">Windows Form 應用程式上執行其本身。</span><span class="sxs-lookup"><span data-stu-id="32d32-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="32d32-116">不過，Visual Basic 編譯器會自動產生`Main`程序，例如應用程式，而且您不需要撰寫一個。</span><span class="sxs-lookup"><span data-stu-id="32d32-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="32d32-117">類別庫不需要`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="32d32-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="32d32-118">其中包括 Windows 控制項程式庫和 Web 控制項程式庫。</span><span class="sxs-lookup"><span data-stu-id="32d32-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="32d32-119">Web 應用程式會部署為類別庫。</span><span class="sxs-lookup"><span data-stu-id="32d32-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="32d32-120">宣告的主要程序</span><span class="sxs-lookup"><span data-stu-id="32d32-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="32d32-121">有四種方式來宣告`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="32d32-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="32d32-122">它可以接受引數，和它可以在或不傳回值。</span><span class="sxs-lookup"><span data-stu-id="32d32-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32d32-123">如果您宣告`Main`在類別中，您必須使用`Shared`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="32d32-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="32d32-124">在模組中，`Main`不需要為`Shared`。</span><span class="sxs-lookup"><span data-stu-id="32d32-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="32d32-125">最簡單的方式是宣告`Sub`不接受引數或傳回值的程序。</span><span class="sxs-lookup"><span data-stu-id="32d32-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="32d32-126">`Main`也可以傳回`Integer`值，作業系統會使用與結束碼為您的程式。</span><span class="sxs-lookup"><span data-stu-id="32d32-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="32d32-127">其他程式可以藉由檢查 Windows ERRORLEVEL 值測試這段程式碼。</span><span class="sxs-lookup"><span data-stu-id="32d32-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="32d32-128">若要傳回的結束代碼，您必須宣告`Main`為`Function`程序，而不是`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="32d32-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   <span data-ttu-id="32d32-129">`Main`也可以採用`String`做為引數的陣列。</span><span class="sxs-lookup"><span data-stu-id="32d32-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="32d32-130">陣列中的每個字串可包含一個用來叫用您的程式命令列引數。</span><span class="sxs-lookup"><span data-stu-id="32d32-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="32d32-131">您可以採取不同的動作，取決於其值。</span><span class="sxs-lookup"><span data-stu-id="32d32-131">You can take different actions depending on their values.</span></span>  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   <span data-ttu-id="32d32-132">您可以宣告`Main`檢查命令列引數，但不會傳回結束程式碼，如下所示。</span><span class="sxs-lookup"><span data-stu-id="32d32-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="32d32-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="32d32-133">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="32d32-134">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="32d32-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="32d32-135">/main</span><span class="sxs-lookup"><span data-stu-id="32d32-135">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="32d32-136">Shared</span><span class="sxs-lookup"><span data-stu-id="32d32-136">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="32d32-137">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="32d32-137">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="32d32-138">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="32d32-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="32d32-139">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="32d32-139">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="32d32-140">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="32d32-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
