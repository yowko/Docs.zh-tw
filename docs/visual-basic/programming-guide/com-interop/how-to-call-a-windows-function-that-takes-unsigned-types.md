---
title: 如何：呼叫使用不帶正負號類型的 Windows 函式 (Visual Basic)
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
ms.openlocfilehash: afec9965c4ff728094e901eb4924ac94c432b300
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643022"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="fbc90-102">如何：呼叫使用不帶正負號類型的 Windows 函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbc90-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="fbc90-103">如果您正在耗用類別、 模組或具有不帶正負號的整數類型的成員的結構，您可以存取這些成員與 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="fbc90-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="fbc90-104">若要呼叫 Windows 函式採用不帶正負號的類型</span><span class="sxs-lookup"><span data-stu-id="fbc90-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="fbc90-105">使用[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)告訴 Visual Basic 的程式庫會保存函式、 其名稱為該文件庫中，其呼叫的順序為何，以及如何呼叫它時，將字串轉換。</span><span class="sxs-lookup"><span data-stu-id="fbc90-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="fbc90-106">在`Declare`陳述式中，使用`UInteger`， `ULong`， `UShort`，或`Byte`視需要針對每個參數具有不帶正負號的類型。</span><span class="sxs-lookup"><span data-stu-id="fbc90-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="fbc90-107">若要尋找的名稱和值的常數，它會使用呼叫 Windows 函式，請參閱文件。</span><span class="sxs-lookup"><span data-stu-id="fbc90-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="fbc90-108">其中許多 WinUser.h 檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="fbc90-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="fbc90-109">宣告在程式碼中必要的常數。</span><span class="sxs-lookup"><span data-stu-id="fbc90-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="fbc90-110">許多 Windows 常數 32 位元不帶正負號的值，而且您應該將這些宣告`As``UInteger`。</span><span class="sxs-lookup"><span data-stu-id="fbc90-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="fbc90-111">以一般方式呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="fbc90-111">Call the function in the normal way.</span></span> <span data-ttu-id="fbc90-112">下列範例會呼叫 Windows 函式`MessageBox`，其可接受不帶正負號的整數引數。</span><span class="sxs-lookup"><span data-stu-id="fbc90-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
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
  
     <span data-ttu-id="fbc90-113">您可以測試函式`messageThroughWindows`為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="fbc90-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="fbc90-114">`UInteger`， `ULong`， `UShort`，和`SByte`資料類型不屬於[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（cls） 標準，所以符合 CLS 標準的程式碼無法使用的元件，使用它們。</span><span class="sxs-lookup"><span data-stu-id="fbc90-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="fbc90-115">呼叫 unmanaged 程式碼，例如 Windows 應用程式開發介面 (API)，會公開您的程式碼有潛在的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="fbc90-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="fbc90-116">呼叫 Windows API 需要 unmanaged 程式碼權限，這可能會影響在部分信任情況下執行。</span><span class="sxs-lookup"><span data-stu-id="fbc90-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="fbc90-117">如需詳細資訊，請參閱<xref:System.Security.Permissions.SecurityPermission>和[程式碼存取權限](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675)。</span><span class="sxs-lookup"><span data-stu-id="fbc90-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc90-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbc90-118">See Also</span></span>  
 [<span data-ttu-id="fbc90-119">資料類型</span><span class="sxs-lookup"><span data-stu-id="fbc90-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="fbc90-120">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="fbc90-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="fbc90-121">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="fbc90-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [<span data-ttu-id="fbc90-122">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="fbc90-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="fbc90-123">逐步解說：呼叫 Windows API</span><span class="sxs-lookup"><span data-stu-id="fbc90-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
