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
ms.openlocfilehash: 641edd2d0e0dde5f509c8fa77ccf65358fa76a31
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833663"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="6b4be-102">Visual Basic 中的 Main 程序</span><span class="sxs-lookup"><span data-stu-id="6b4be-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="6b4be-103">每個 Visual Basic 應用程式必須包含呼叫的程序`Main`。</span><span class="sxs-lookup"><span data-stu-id="6b4be-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="6b4be-104">起始點和應用程式的整體控制，就會作為此程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="6b4be-105">.NET Framework 會呼叫您`Main`時它已載入您的應用程式，並已準備好將控制權傳給它的程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="6b4be-106">除非您要建立的 Windows Forms 應用程式，您必須撰寫`Main`上執行自己的應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="6b4be-107">`Main` 包含會先執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="6b4be-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="6b4be-108">在  `Main`，您可以判斷哪一個表單是在程式啟動時，第一次載入、 找出您的應用程式的複本是否已執行系統上，為您的應用程式中，建立一組變數或開啟應用程式所需的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6b4be-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="6b4be-109">在主要程序的需求</span><span class="sxs-lookup"><span data-stu-id="6b4be-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="6b4be-110">（通常具有副檔名.exe) 單獨執行的檔案必須包含`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="6b4be-111">無法在執行它自己的程式庫 （例如.dll 副檔名)，而且不需要`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="6b4be-112">您可以建立不同類型的專案的需求如下所示：</span><span class="sxs-lookup"><span data-stu-id="6b4be-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="6b4be-113">主控台應用程式上執行其本身，而您則必須提供至少一個`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="6b4be-114">。</span><span class="sxs-lookup"><span data-stu-id="6b4be-114">.</span></span>  
  
-   <span data-ttu-id="6b4be-115">Windows Forms 應用程式上執行自己。</span><span class="sxs-lookup"><span data-stu-id="6b4be-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="6b4be-116">不過，Visual Basic 編譯器會自動產生`Main`程序，在這類應用程式，而且您不需要撰寫一個。</span><span class="sxs-lookup"><span data-stu-id="6b4be-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="6b4be-117">類別庫不需要`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="6b4be-118">其中包括 Windows 控制項程式庫和 Web 控制項程式庫。</span><span class="sxs-lookup"><span data-stu-id="6b4be-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="6b4be-119">Web 應用程式會部署為類別庫。</span><span class="sxs-lookup"><span data-stu-id="6b4be-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="6b4be-120">宣告的 Main 程序</span><span class="sxs-lookup"><span data-stu-id="6b4be-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="6b4be-121">有四種方式來宣告`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="6b4be-122">它可以接受引數，和與否，它可以傳回值。</span><span class="sxs-lookup"><span data-stu-id="6b4be-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b4be-123">如果您宣告`Main`在類別中，您必須使用`Shared`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6b4be-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="6b4be-124">在模組中，`Main`不需要是`Shared`。</span><span class="sxs-lookup"><span data-stu-id="6b4be-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="6b4be-125">最簡單的方式是將宣告`Sub`不接受引數或傳回值的程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="6b4be-126">`Main` 也可以傳回`Integer`作業系統做為您的程式結束代碼的值。</span><span class="sxs-lookup"><span data-stu-id="6b4be-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="6b4be-127">其他程式可以測試此程式碼檢查 Windows ERRORLEVEL 值。</span><span class="sxs-lookup"><span data-stu-id="6b4be-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="6b4be-128">若要傳回的結束代碼，您必須宣告`Main`作為`Function`程序，而不是`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="6b4be-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
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
  
-   <span data-ttu-id="6b4be-129">`Main` 也可以採用`String`做為引數的陣列。</span><span class="sxs-lookup"><span data-stu-id="6b4be-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="6b4be-130">陣列中的每個字串會包含用來叫用程式的命令列引數之一。</span><span class="sxs-lookup"><span data-stu-id="6b4be-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="6b4be-131">您可以採取不同的動作，取決於其值。</span><span class="sxs-lookup"><span data-stu-id="6b4be-131">You can take different actions depending on their values.</span></span>  
  
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
  
-   <span data-ttu-id="6b4be-132">您可以宣告`Main`檢查命令列引數，但不會傳回結束程式碼，如下所示。</span><span class="sxs-lookup"><span data-stu-id="6b4be-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b4be-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b4be-133">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="6b4be-134">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="6b4be-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="6b4be-135">/main</span><span class="sxs-lookup"><span data-stu-id="6b4be-135">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="6b4be-136">Shared</span><span class="sxs-lookup"><span data-stu-id="6b4be-136">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="6b4be-137">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b4be-137">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="6b4be-138">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b4be-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="6b4be-139">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="6b4be-139">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="6b4be-140">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="6b4be-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
