---
title: Visual Basic 中的 Main 程序
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 19c6fcb04a373d782db3deafc732f69bf20e7f0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962765"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="fd4b4-102">Visual Basic 中的 Main 程序</span><span class="sxs-lookup"><span data-stu-id="fd4b4-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="fd4b4-103">每個 Visual Basic 應用程式都必須包含`Main`名為的程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="fd4b4-104">此程式可做為您應用程式的起點和整體控制。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="fd4b4-105">.NET Framework 會在載入`Main`您的應用程式並準備好將控制權傳遞給它時, 呼叫您的程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="fd4b4-106">除非您要建立 Windows Forms 應用程式, 否則必須針對自己`Main`執行的應用程式撰寫程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="fd4b4-107">`Main`包含第一個執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="fd4b4-108">在`Main`中, 您可以決定要在程式啟動時先載入哪一個表單、找出應用程式的複本是否已經在系統上執行、為您的應用程式建立一組變數, 或是開啟應用程式所需的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="fd4b4-109">主要程式的需求</span><span class="sxs-lookup"><span data-stu-id="fd4b4-109">Requirements for the Main Procedure</span></span>
 <span data-ttu-id="fd4b4-110">本身本身執行的檔案 (通常副檔名為 .exe) 必須包含一個`Main`程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="fd4b4-111">程式庫 (例如, 副檔名為 .dll) 本身不會執行, 也不需要`Main`程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="fd4b4-112">您可以建立的不同專案類型的需求如下:</span><span class="sxs-lookup"><span data-stu-id="fd4b4-112">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="fd4b4-113">主控台應用程式會自行執行, 而且您必須至少提供一個`Main`程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="fd4b4-114">Windows Forms 應用程式會自行執行。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-114">Windows Forms applications run on their own.</span></span> <span data-ttu-id="fd4b4-115">不過, Visual Basic 編譯器會自動在這`Main`類應用程式中產生程式, 而您不需要撰寫一個。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-115">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="fd4b4-116">類別庫不需要`Main`程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-116">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="fd4b4-117">其中包括 Windows 控制項程式庫和 Web 控制項程式庫。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-117">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="fd4b4-118">Web 應用程式會部署為類別庫。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-118">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="fd4b4-119">宣告 Main 程式</span><span class="sxs-lookup"><span data-stu-id="fd4b4-119">Declaring the Main Procedure</span></span>
 <span data-ttu-id="fd4b4-120">有四種方式可以`Main`宣告程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-120">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="fd4b4-121">它可以接受引數, 也可以傳回值。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-121">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="fd4b4-122">如果您`Main`在類別中宣告, 則必須`Shared`使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-122">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="fd4b4-123">在模組中, `Main`不需要是。 `Shared`</span><span class="sxs-lookup"><span data-stu-id="fd4b4-123">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="fd4b4-124">最簡單的方式是`Sub`宣告不接受引數或傳回值的程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-124">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="fd4b4-125">`Main`也可以傳回`Integer`值, 以供作業系統用來做為程式的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-125">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="fd4b4-126">其他程式則可以藉由檢查 Windows ERRORLEVEL 值來測試此程式碼。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-126">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="fd4b4-127">若要傳回結束代碼, 您必須`Main`將宣告`Function`為程式, 而不`Sub`是程式。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-127">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

    ```vb
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

- <span data-ttu-id="fd4b4-128">`Main`也可以採用`String`陣列做為引數。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-128">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="fd4b4-129">陣列中的每個字串都包含用來叫用程式的其中一個命令列引數。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-129">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="fd4b4-130">您可以根據它們的值來採取不同的動作。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-130">You can take different actions depending on their values.</span></span>

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
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

- <span data-ttu-id="fd4b4-131">您可以宣告`Main`來檢查命令列引數, 但不會傳回結束代碼, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="fd4b4-131">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a><span data-ttu-id="fd4b4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd4b4-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="fd4b4-133">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="fd4b4-133">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="fd4b4-134">/main</span><span class="sxs-lookup"><span data-stu-id="fd4b4-134">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="fd4b4-135">Shared</span><span class="sxs-lookup"><span data-stu-id="fd4b4-135">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="fd4b4-136">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="fd4b4-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="fd4b4-137">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="fd4b4-137">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="fd4b4-138">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="fd4b4-138">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="fd4b4-139">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="fd4b4-139">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
