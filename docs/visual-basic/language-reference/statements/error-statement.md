---
title: Error 陳述式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cd3245fd3e9e62b1b6443e9787c97808a0d179d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="error-statement"></a><span data-ttu-id="75f4a-102">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="75f4a-102">Error Statement</span></span>
<span data-ttu-id="75f4a-103">模擬的錯誤。</span><span class="sxs-lookup"><span data-stu-id="75f4a-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f4a-104">語法</span><span class="sxs-lookup"><span data-stu-id="75f4a-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="75f4a-105">組件</span><span class="sxs-lookup"><span data-stu-id="75f4a-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="75f4a-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="75f4a-106">Required.</span></span> <span data-ttu-id="75f4a-107">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="75f4a-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75f4a-108">備註</span><span class="sxs-lookup"><span data-stu-id="75f4a-108">Remarks</span></span>  
 <span data-ttu-id="75f4a-109">`Error`回溯相容性支援陳述式。</span><span class="sxs-lookup"><span data-stu-id="75f4a-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="75f4a-110">在新的程式碼，特別是在建立物件時，使用`Err`物件的`Raise`方法來產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="75f4a-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="75f4a-111">如果`errornumber`定義，`Error`陳述式之後的內容會呼叫錯誤處理常式`Err`物件會指定下列的預設值：</span><span class="sxs-lookup"><span data-stu-id="75f4a-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="75f4a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="75f4a-112">Property</span></span>|<span data-ttu-id="75f4a-113">值</span><span class="sxs-lookup"><span data-stu-id="75f4a-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="75f4a-114">指定為引數的值`Error`陳述式。</span><span class="sxs-lookup"><span data-stu-id="75f4a-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="75f4a-115">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="75f4a-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="75f4a-116">目前的 Visual Basic 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="75f4a-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="75f4a-117">字串對應至傳回值的運算式`Error`函式指定`Number`，如果這個字串已存在。</span><span class="sxs-lookup"><span data-stu-id="75f4a-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="75f4a-118">如果字串不存在，`Description`包含零長度字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="75f4a-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="75f4a-119">完整的磁碟機、 路徑和檔案名稱的適當的 Visual Basic 說明檔案。</span><span class="sxs-lookup"><span data-stu-id="75f4a-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="75f4a-120">適當的 Visual Basic 說明檔案內容識別碼對應至錯誤`Number`屬性。</span><span class="sxs-lookup"><span data-stu-id="75f4a-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="75f4a-121">是零。</span><span class="sxs-lookup"><span data-stu-id="75f4a-121">Zero.</span></span>|  
  
 <span data-ttu-id="75f4a-122">如果錯誤處理常式不存在，或如果沒有啟用，建立並從顯示的錯誤訊息`Err`物件屬性。</span><span class="sxs-lookup"><span data-stu-id="75f4a-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75f4a-123">某些 Visual Basic 主機應用程式無法建立物件。</span><span class="sxs-lookup"><span data-stu-id="75f4a-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="75f4a-124">請參閱主應用程式的文件，以判斷它是否可以建立類別和物件。</span><span class="sxs-lookup"><span data-stu-id="75f4a-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75f4a-125">範例</span><span class="sxs-lookup"><span data-stu-id="75f4a-125">Example</span></span>  
 <span data-ttu-id="75f4a-126">這個範例會使用`Error`陳述式產生錯誤代碼 11。</span><span class="sxs-lookup"><span data-stu-id="75f4a-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="75f4a-127">需求</span><span class="sxs-lookup"><span data-stu-id="75f4a-127">Requirements</span></span>  
 <span data-ttu-id="75f4a-128">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="75f4a-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="75f4a-129">**組件：** Visual Basic Runtime Library （位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="75f4a-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f4a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75f4a-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [<span data-ttu-id="75f4a-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="75f4a-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [<span data-ttu-id="75f4a-132">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="75f4a-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="75f4a-133">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="75f4a-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
