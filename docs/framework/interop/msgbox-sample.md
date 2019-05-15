---
title: MsgBox 範例
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c4100bb3bafdfe141dc746a64ebd8172ebe3bce
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648582"
---
# <a name="msgbox-sample"></a><span data-ttu-id="f5eb5-102">MsgBox 範例</span><span class="sxs-lookup"><span data-stu-id="f5eb5-102">MsgBox Sample</span></span>
<span data-ttu-id="f5eb5-103">此範例示範如何以傳值方式將字串類型傳遞為 In 參數，以及何時使用 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> 和 <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> 欄位。</span><span class="sxs-lookup"><span data-stu-id="f5eb5-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="f5eb5-104">MsgBox 範例會使用下列 Unmanaged 函式和其原始函式宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f5eb5-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="f5eb5-105">從 User32.dll 匯出的 **MessageBox**。</span><span class="sxs-lookup"><span data-stu-id="f5eb5-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="f5eb5-106">在此範例中，`LibWrap` 類別包含 `MsgBoxSample` 類別所呼叫之每個 Unmanaged 函式的 Managed 原型。</span><span class="sxs-lookup"><span data-stu-id="f5eb5-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="f5eb5-107">Managed 原型方法 `MsgBox`、`MsgBox2` 和 `MsgBox3` 有相同 Unmanaged 函式的不同宣告。</span><span class="sxs-lookup"><span data-stu-id="f5eb5-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="f5eb5-108">`MsgBox2` 的宣告會在訊息方塊中產生不正確的輸出，因為指定為 ANSI 的字元類型與進入點 `MessageBoxW` (即 Unicode 函式的名稱) 不相符。</span><span class="sxs-lookup"><span data-stu-id="f5eb5-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="f5eb5-109">`MsgBox3` 的宣告會在 **EntryPoint**、**CharSet** 與 **ExactSpelling** 欄位之間建立不相符項目。</span><span class="sxs-lookup"><span data-stu-id="f5eb5-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="f5eb5-110">呼叫時，`MsgBox3` 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f5eb5-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="f5eb5-111">如需字串命名和名稱封送處理的詳細資訊，請參閱[指定字元集](specifying-a-character-set.md)。</span><span class="sxs-lookup"><span data-stu-id="f5eb5-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="f5eb5-112">宣告原型</span><span class="sxs-lookup"><span data-stu-id="f5eb5-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="f5eb5-113">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="f5eb5-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="f5eb5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5eb5-114">See also</span></span>

- [<span data-ttu-id="f5eb5-115">封送處理字串</span><span class="sxs-lookup"><span data-stu-id="f5eb5-115">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="f5eb5-116">字串的預設封送處理</span><span class="sxs-lookup"><span data-stu-id="f5eb5-116">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="f5eb5-117">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="f5eb5-117">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="f5eb5-118">指定字元集</span><span class="sxs-lookup"><span data-stu-id="f5eb5-118">Specifying a Character Set</span></span>](specifying-a-character-set.md)
