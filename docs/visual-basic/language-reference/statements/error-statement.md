---
title: Error 陳述式
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
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351241"
---
# <a name="error-statement"></a><span data-ttu-id="48736-102">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="48736-102">Error Statement</span></span>
<span data-ttu-id="48736-103">模擬發生錯誤的次數。</span><span class="sxs-lookup"><span data-stu-id="48736-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48736-104">語法</span><span class="sxs-lookup"><span data-stu-id="48736-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="48736-105">組件</span><span class="sxs-lookup"><span data-stu-id="48736-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="48736-106">必要。</span><span class="sxs-lookup"><span data-stu-id="48736-106">Required.</span></span> <span data-ttu-id="48736-107">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="48736-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48736-108">備註</span><span class="sxs-lookup"><span data-stu-id="48736-108">Remarks</span></span>  
 <span data-ttu-id="48736-109">支援 `Error` 語句以提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="48736-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="48736-110">在新程式碼中，尤其是在建立物件時，請使用 `Err` 物件的 `Raise` 方法來產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="48736-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="48736-111">如果定義了 `errornumber`，`Error` 語句會在將下列預設值指派給 `Err` 物件的屬性之後，呼叫錯誤處理常式：</span><span class="sxs-lookup"><span data-stu-id="48736-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="48736-112">屬性</span><span class="sxs-lookup"><span data-stu-id="48736-112">Property</span></span>|<span data-ttu-id="48736-113">值</span><span class="sxs-lookup"><span data-stu-id="48736-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="48736-114">指定為 `Error` 語句之引數的值。</span><span class="sxs-lookup"><span data-stu-id="48736-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="48736-115">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="48736-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="48736-116">目前 Visual Basic 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="48736-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="48736-117">對應至指定 `Number`之 `Error` 函數傳回值的字串運算式（如果這個字串存在）。</span><span class="sxs-lookup"><span data-stu-id="48736-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="48736-118">如果字串不存在，`Description` 會包含長度為零的字串（""）。</span><span class="sxs-lookup"><span data-stu-id="48736-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="48736-119">適當 Visual Basic 說明檔的完整磁片磁碟機、路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="48736-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="48736-120">適當的 Visual Basic 說明 `Number` 屬性對應之錯誤的說明檔內容識別碼。</span><span class="sxs-lookup"><span data-stu-id="48736-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="48736-121">零.</span><span class="sxs-lookup"><span data-stu-id="48736-121">Zero.</span></span>|  
  
 <span data-ttu-id="48736-122">如果沒有錯誤處理常式存在，或未啟用，則會建立錯誤訊息，並顯示在 `Err` 物件屬性中。</span><span class="sxs-lookup"><span data-stu-id="48736-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48736-123">某些 Visual Basic 主應用程式無法建立物件。</span><span class="sxs-lookup"><span data-stu-id="48736-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="48736-124">請參閱主機應用程式的檔，以判斷它是否可以建立類別和物件。</span><span class="sxs-lookup"><span data-stu-id="48736-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48736-125">範例</span><span class="sxs-lookup"><span data-stu-id="48736-125">Example</span></span>  
 <span data-ttu-id="48736-126">這個範例會使用 `Error` 語句來產生錯誤號碼11。</span><span class="sxs-lookup"><span data-stu-id="48736-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="48736-127">需求</span><span class="sxs-lookup"><span data-stu-id="48736-127">Requirements</span></span>  
 <span data-ttu-id="48736-128">**命名空間：** [Microsoft.](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="48736-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="48736-129">**元件：** Visual Basic 執行時間程式庫（在 Microsoft 中）</span><span class="sxs-lookup"><span data-stu-id="48736-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48736-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="48736-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="48736-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="48736-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="48736-132">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="48736-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="48736-133">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="48736-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
