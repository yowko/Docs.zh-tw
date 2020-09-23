---
title: 主要程序
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: d6708ee13963aaae43a73b159032f64f0fffac10
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072206"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="345f9-102">Visual Basic 中的 Main 程序</span><span class="sxs-lookup"><span data-stu-id="345f9-102">Main Procedure in Visual Basic</span></span>

<span data-ttu-id="345f9-103">每個 Visual Basic 的應用程式都必須包含一個稱為的程式 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="345f9-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="345f9-104">此程式可作為應用程式的起點和整體控制。</span><span class="sxs-lookup"><span data-stu-id="345f9-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="345f9-105">`Main`當程式載入您的應用程式，並準備好將控制權傳遞給它時，.NET Framework 會呼叫您的程式。</span><span class="sxs-lookup"><span data-stu-id="345f9-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="345f9-106">除非您要建立 Windows Forms 應用程式，否則您必須 `Main` 針對自己執行的應用程式撰寫程式。</span><span class="sxs-lookup"><span data-stu-id="345f9-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="345f9-107">`Main` 包含先執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="345f9-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="345f9-108">在中 `Main` ，您可以決定要在程式啟動時先載入的表單、找出應用程式的複本是否已在系統上執行、為您的應用程式建立一組變數，或是開啟應用程式所需的資料庫。</span><span class="sxs-lookup"><span data-stu-id="345f9-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="345f9-109">主要程式的需求</span><span class="sxs-lookup"><span data-stu-id="345f9-109">Requirements for the Main Procedure</span></span>

 <span data-ttu-id="345f9-110">在自己的 (上執行的檔案通常使用副檔名) 必須包含程式 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="345f9-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="345f9-111">程式庫 (例如副檔名為 .dll) 不會自行執行，也不需要程式 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="345f9-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="345f9-112">您可以建立的不同專案類型的需求如下：</span><span class="sxs-lookup"><span data-stu-id="345f9-112">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="345f9-113">主控台應用程式會自行執行，而且您必須至少提供一個程式 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="345f9-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="345f9-114">Windows Forms 的應用程式會自行執行。</span><span class="sxs-lookup"><span data-stu-id="345f9-114">Windows Forms applications run on their own.</span></span> <span data-ttu-id="345f9-115">不過，Visual Basic 編譯器會 `Main` 在這類應用程式中自動產生程式，而您不需要撰寫一個程式。</span><span class="sxs-lookup"><span data-stu-id="345f9-115">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="345f9-116">類別庫不需要程式 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="345f9-116">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="345f9-117">這些包括 Windows 控制項程式庫和 Web 控制項程式庫。</span><span class="sxs-lookup"><span data-stu-id="345f9-117">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="345f9-118">Web 應用程式會部署為類別庫。</span><span class="sxs-lookup"><span data-stu-id="345f9-118">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="345f9-119">宣告 Main 程式</span><span class="sxs-lookup"><span data-stu-id="345f9-119">Declaring the Main Procedure</span></span>

 <span data-ttu-id="345f9-120">有四種方式可以宣告程式 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="345f9-120">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="345f9-121">它可以採用引數，也可以傳回值。</span><span class="sxs-lookup"><span data-stu-id="345f9-121">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="345f9-122">如果您 `Main` 在類別中宣告，則必須使用 `Shared` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="345f9-122">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="345f9-123">在模組中， `Main` 不需要是 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="345f9-123">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="345f9-124">最簡單的方式是宣告不 `Sub` 採用引數或傳回值的程式。</span><span class="sxs-lookup"><span data-stu-id="345f9-124">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="345f9-125">`Main` 也可以傳回 `Integer` 值，讓作業系統用來作為程式的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="345f9-125">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="345f9-126">其他程式則可以藉由檢查 Windows ERRORLEVEL 值來測試此程式碼。</span><span class="sxs-lookup"><span data-stu-id="345f9-126">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="345f9-127">若要傳回結束代碼，您必須將宣告為程式， `Main` `Function` 而不是程式 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="345f9-127">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

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

- <span data-ttu-id="345f9-128">`Main` 也可以採用 `String` 陣列作為引數。</span><span class="sxs-lookup"><span data-stu-id="345f9-128">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="345f9-129">陣列中的每個字串都包含用來叫用程式的其中一個命令列引數。</span><span class="sxs-lookup"><span data-stu-id="345f9-129">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="345f9-130">您可以根據其值採取不同的動作。</span><span class="sxs-lookup"><span data-stu-id="345f9-130">You can take different actions depending on their values.</span></span>

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

- <span data-ttu-id="345f9-131">您可以宣告 `Main` 以檢查命令列引數，但不會傳回結束代碼，如下所示。</span><span class="sxs-lookup"><span data-stu-id="345f9-131">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

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
  
## <a name="see-also"></a><span data-ttu-id="345f9-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="345f9-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="345f9-133">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="345f9-133">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="345f9-134">-main</span><span class="sxs-lookup"><span data-stu-id="345f9-134">-main</span></span>](../../reference/command-line-compiler/main.md)
- <span data-ttu-id="345f9-135">[共用][](../../language-reference/modifiers/shared.md)</span><span class="sxs-lookup"><span data-stu-id="345f9-135">[Shared](../../language-reference/modifiers/shared.md)</span></span>
- [<span data-ttu-id="345f9-136">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="345f9-136">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="345f9-137">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="345f9-137">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="345f9-138">整數資料類型</span><span class="sxs-lookup"><span data-stu-id="345f9-138">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="345f9-139">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="345f9-139">String Data Type</span></span>](../../language-reference/data-types/string-data-type.md)
