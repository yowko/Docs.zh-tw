---
title: HOW TO：呼叫採用不帶正負號類型的 Windows 函式（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
ms.openlocfilehash: 97075fb6149ed8c0ce06318d0e5bb6f01b841f30
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053319"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="d1a8e-102">HOW TO：呼叫採用不帶正負號類型的 Windows 函式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d1a8e-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="d1a8e-103">如果您使用的類別、模組或結構具有不帶正負號整數類型的成員，您可以使用 Visual Basic 來存取這些成員。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="d1a8e-104">呼叫採用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="d1a8e-104">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="d1a8e-105">使用[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)來告訴 Visual Basic 哪一個程式庫包含函式、它在該程式庫中的名稱、其呼叫順序為何，以及如何在呼叫它時轉換字串。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="d1a8e-106">`Byte` `UShort` `ULong` `UInteger`在語句中，針對具有不帶正負號類型的每個參數，使用、、或。 `Declare`</span><span class="sxs-lookup"><span data-stu-id="d1a8e-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="d1a8e-107">請參閱您所呼叫之 Windows 函式的檔，以尋找其所使用之常數的名稱和值。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="d1a8e-108">其中有許多都是在 WinUser 檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-108">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="d1a8e-109">在您的程式碼中宣告必要的常數。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="d1a8e-110">許多 Windows 常數都是32位不帶正負號的值，您`As UInteger`應該將它們宣告為。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="d1a8e-111">以正常方式呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-111">Call the function in the normal way.</span></span> <span data-ttu-id="d1a8e-112">下列範例會呼叫 Windows `MessageBox`函式，它會採用不帶正負號的整數引數。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

    ```vb
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

     <span data-ttu-id="d1a8e-113">您可以使用下列程式`messageThroughWindows`代碼來測試函數。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-113">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="d1a8e-114">`UInteger`、 、和`UShort`資料類型不是[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS）的一部分，因此符合 CLS 標準的程式碼無法取用使用它們的元件。 `SByte` `ULong`</span><span class="sxs-lookup"><span data-stu-id="d1a8e-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d1a8e-115">呼叫非受控碼（例如 Windows 應用程式開發介面（API））會讓您的程式碼暴露于潛在的安全性風險下。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d1a8e-116">呼叫 Windows API 需要未受管理的程式碼許可權，這可能會影響在部分信任情況下的執行。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="d1a8e-117">如需詳細資訊， <xref:System.Security.Permissions.SecurityPermission>請參閱和程式[代碼存取權限](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d1a8e-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1a8e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1a8e-118">See also</span></span>

- [<span data-ttu-id="d1a8e-119">資料類型</span><span class="sxs-lookup"><span data-stu-id="d1a8e-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d1a8e-120">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="d1a8e-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="d1a8e-121">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="d1a8e-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="d1a8e-122">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="d1a8e-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="d1a8e-123">逐步解說：呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="d1a8e-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
