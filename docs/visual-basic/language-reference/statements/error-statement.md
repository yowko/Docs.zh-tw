---
title: Error 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 84fce92183228cbfa5554a3ba45770a86e83bff5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400623"
---
# <a name="error-statement"></a><span data-ttu-id="c332e-102">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="c332e-102">Error Statement</span></span>
<span data-ttu-id="c332e-103">模擬錯誤的相符項目。</span><span class="sxs-lookup"><span data-stu-id="c332e-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c332e-104">語法</span><span class="sxs-lookup"><span data-stu-id="c332e-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="c332e-105">組件</span><span class="sxs-lookup"><span data-stu-id="c332e-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="c332e-106">必要。</span><span class="sxs-lookup"><span data-stu-id="c332e-106">Required.</span></span> <span data-ttu-id="c332e-107">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="c332e-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c332e-108">備註</span><span class="sxs-lookup"><span data-stu-id="c332e-108">Remarks</span></span>  
 <span data-ttu-id="c332e-109">`Error`回溯相容性支援陳述式。</span><span class="sxs-lookup"><span data-stu-id="c332e-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="c332e-110">在新的程式碼，尤其是在建立物件時，使用`Err`物件的`Raise`方法來產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="c332e-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="c332e-111">如果`errornumber`定義，則`Error`陳述式會呼叫錯誤處理常式的屬性之後`Err`物件會指派預設值如下：</span><span class="sxs-lookup"><span data-stu-id="c332e-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="c332e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c332e-112">Property</span></span>|<span data-ttu-id="c332e-113">值</span><span class="sxs-lookup"><span data-stu-id="c332e-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="c332e-114">指定為引數的值`Error`陳述式。</span><span class="sxs-lookup"><span data-stu-id="c332e-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="c332e-115">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="c332e-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="c332e-116">目前的 Visual Basic 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="c332e-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="c332e-117">字串對應至的傳回值的運算式`Error`函式指定`Number`，如果這個字串已存在。</span><span class="sxs-lookup"><span data-stu-id="c332e-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="c332e-118">如果字串不存在，`Description`包含零長度字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="c332e-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="c332e-119">完整格式的磁碟機、 路徑和適當的 Visual Basic 說明檔的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c332e-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="c332e-120">適當的 Visual Basic 說明檔內容識別碼對應至錯誤`Number`屬性。</span><span class="sxs-lookup"><span data-stu-id="c332e-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="c332e-121">為零。</span><span class="sxs-lookup"><span data-stu-id="c332e-121">Zero.</span></span>|  
  
 <span data-ttu-id="c332e-122">如果沒有錯誤處理常式存在，或如果沒有任何已啟用，建立並從顯示的錯誤訊息`Err`物件屬性。</span><span class="sxs-lookup"><span data-stu-id="c332e-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c332e-123">某些 Visual Basic 主應用程式無法建立物件。</span><span class="sxs-lookup"><span data-stu-id="c332e-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="c332e-124">請參閱主應用程式的文件，以判斷它是否可以建立類別和物件。</span><span class="sxs-lookup"><span data-stu-id="c332e-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c332e-125">範例</span><span class="sxs-lookup"><span data-stu-id="c332e-125">Example</span></span>  
 <span data-ttu-id="c332e-126">這個範例會使用`Error`陳述式產生錯誤代碼 11。</span><span class="sxs-lookup"><span data-stu-id="c332e-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="c332e-127">需求</span><span class="sxs-lookup"><span data-stu-id="c332e-127">Requirements</span></span>  
 <span data-ttu-id="c332e-128">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="c332e-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="c332e-129">**組件：** Visual Basic 執行階段程式庫 （位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="c332e-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c332e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c332e-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [<span data-ttu-id="c332e-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="c332e-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [<span data-ttu-id="c332e-132">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="c332e-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="c332e-133">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c332e-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
