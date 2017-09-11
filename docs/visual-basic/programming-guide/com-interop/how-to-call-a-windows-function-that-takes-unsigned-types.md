---
title: "如何︰ 呼叫 Windows 函式會採用不帶正負號的類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Windows functions, calling
- unsigned data types
- UShort data type, using
- functions [Visual Basic], calling Windows functions
- ULong data type, using
- UInteger data type, using
- data types [Visual Basic], using
- unsigned types
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types, using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7b6b1d46b6ccab0ec8d63fb8b7d8722b518b81b4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="58029-102">如何：呼叫使用不帶正負號類型的 Windows 函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58029-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="58029-103">如果您使用的類別、 模組或具有不帶正負號的整數類型的成員的結構，您可以存取這些成員與[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="58029-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="58029-104">若要呼叫 Windows 函式採用不帶正負號的型別</span><span class="sxs-lookup"><span data-stu-id="58029-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="58029-105">使用[宣告陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)告知[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式庫包含函式、 其名稱為該文件庫中，其呼叫的順序為何，以及如何將字串轉換呼叫它時。</span><span class="sxs-lookup"><span data-stu-id="58029-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="58029-106">在`Declare`陳述式中，使用`UInteger`， `ULong`， `UShort`，或`Byte`視需要針對每個參數具有不帶正負號的類型。</span><span class="sxs-lookup"><span data-stu-id="58029-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="58029-107">若要尋找的名稱和值的常數，它會使用呼叫 Windows 函式，請參閱文件。</span><span class="sxs-lookup"><span data-stu-id="58029-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="58029-108">多個 WinUser.h 檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="58029-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="58029-109">宣告在程式碼中必要的常數。</span><span class="sxs-lookup"><span data-stu-id="58029-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="58029-110">許多 Windows 常數是 32 位元不帶正負號的值，以及您應該將這些宣告`As``UInteger`。</span><span class="sxs-lookup"><span data-stu-id="58029-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="58029-111">以一般方式呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="58029-111">Call the function in the normal way.</span></span> <span data-ttu-id="58029-112">下列範例會呼叫 Windows 函式`MessageBox`，後者會採用不帶正負號的整數引數。</span><span class="sxs-lookup"><span data-stu-id="58029-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
    ```  
    Public Class windowsMessage  
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (  
            ByVal hWnd As Integer,   
            ByVal lpText As String,   
            ByVal lpCaption As String,   
            ByVal uType As UInteger) As Integer  
        Private Const MB_OK As UInteger = 0  
        Private Const MB_ICONEXCLAMATION As UInteger = &H30  
        Private Const IDOK As UInteger = 1  
        Private Const IDCLOSE As UInteger = 8  
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION  
        Public Function messageThroughWindows() As String  
            Dim r As Integer = mb(0, "Click OK if you see this!",   
                "Windows API call", c)  
            Dim s As String = "Windows API MessageBox returned " &  
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &  
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"  
            Return s  
        End Function  
    End Class  
    ```  
  
     <span data-ttu-id="58029-113">您可以測試函式`messageThroughWindows`為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="58029-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="58029-114">`UInteger`， `ULong`， `UShort`，和`SByte`資料類型不屬於[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)，所以符合 CLS 標準的程式碼無法使用它們使用的元件。</span><span class="sxs-lookup"><span data-stu-id="58029-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="58029-115">呼叫 unmanaged 程式碼，例如 Windows 應用程式開發介面 (API)，會公開您的程式碼的潛在安全性風險。</span><span class="sxs-lookup"><span data-stu-id="58029-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="58029-116">呼叫 Windows API 需要 unmanaged 程式碼權限，這可能會影響它在部分信任情況下執行。</span><span class="sxs-lookup"><span data-stu-id="58029-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="58029-117">如需詳細資訊，請參閱<xref:System.Security.Permissions.SecurityPermission>和[程式碼存取權限](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675)。</xref:System.Security.Permissions.SecurityPermission></span><span class="sxs-lookup"><span data-stu-id="58029-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58029-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58029-118">See Also</span></span>  
 <span data-ttu-id="58029-119">[資料型別](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="58029-119">[Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="58029-120"> [整數資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="58029-120"> [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="58029-121"> [UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="58029-121"> [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) </span></span>  
<span data-ttu-id="58029-122"> [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="58029-122"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="58029-123"> [逐步解說：呼叫 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)</span><span class="sxs-lookup"><span data-stu-id="58029-123"> [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)</span></span>
