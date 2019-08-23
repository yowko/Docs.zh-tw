---
title: Error 語句 (Visual Basic)
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
ms.openlocfilehash: 7b926214d3be7f5f57783a8599acf1bb1042f956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944449"
---
# <a name="error-statement"></a><span data-ttu-id="02bb1-102">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="02bb1-102">Error Statement</span></span>
<span data-ttu-id="02bb1-103">模擬發生錯誤的次數。</span><span class="sxs-lookup"><span data-stu-id="02bb1-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02bb1-104">語法</span><span class="sxs-lookup"><span data-stu-id="02bb1-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="02bb1-105">組件</span><span class="sxs-lookup"><span data-stu-id="02bb1-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="02bb1-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="02bb1-106">Required.</span></span> <span data-ttu-id="02bb1-107">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="02bb1-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02bb1-108">備註</span><span class="sxs-lookup"><span data-stu-id="02bb1-108">Remarks</span></span>  
 <span data-ttu-id="02bb1-109">`Error`語句支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="02bb1-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="02bb1-110">在新程式碼中, 尤其是在建立物件`Err`時, `Raise`請使用物件的方法來產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="02bb1-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="02bb1-111">如果`errornumber`已定義, 則`Error`語句會在`Err`物件的屬性被指派下列預設值之後, 呼叫錯誤處理常式:</span><span class="sxs-lookup"><span data-stu-id="02bb1-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="02bb1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="02bb1-112">Property</span></span>|<span data-ttu-id="02bb1-113">值</span><span class="sxs-lookup"><span data-stu-id="02bb1-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="02bb1-114">指定為`Error`語句之引數的值。</span><span class="sxs-lookup"><span data-stu-id="02bb1-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="02bb1-115">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="02bb1-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="02bb1-116">目前 Visual Basic 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="02bb1-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="02bb1-117">對應至指定`Error` `Number`之函式傳回值的字串運算式 (如果這個字串存在)。</span><span class="sxs-lookup"><span data-stu-id="02bb1-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="02bb1-118">如果字串不存在, `Description`則包含長度為零的字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="02bb1-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="02bb1-119">適當 Visual Basic 說明檔的完整磁片磁碟機、路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="02bb1-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="02bb1-120">適當的 Visual Basic 說明檔內容識別碼, 用於對應于`Number`屬性的錯誤。</span><span class="sxs-lookup"><span data-stu-id="02bb1-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="02bb1-121">零.</span><span class="sxs-lookup"><span data-stu-id="02bb1-121">Zero.</span></span>|  
  
 <span data-ttu-id="02bb1-122">如果沒有錯誤處理常式存在, 或未啟用, 則會建立錯誤訊息, 並從`Err`物件屬性顯示。</span><span class="sxs-lookup"><span data-stu-id="02bb1-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02bb1-123">某些 Visual Basic 主應用程式無法建立物件。</span><span class="sxs-lookup"><span data-stu-id="02bb1-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="02bb1-124">請參閱主機應用程式的檔, 以判斷它是否可以建立類別和物件。</span><span class="sxs-lookup"><span data-stu-id="02bb1-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02bb1-125">範例</span><span class="sxs-lookup"><span data-stu-id="02bb1-125">Example</span></span>  
 <span data-ttu-id="02bb1-126">這個範例會使用`Error`語句來產生錯誤號碼11。</span><span class="sxs-lookup"><span data-stu-id="02bb1-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="02bb1-127">需求</span><span class="sxs-lookup"><span data-stu-id="02bb1-127">Requirements</span></span>  
 <span data-ttu-id="02bb1-128">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="02bb1-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="02bb1-129">**Assembly**Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="02bb1-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02bb1-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02bb1-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="02bb1-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="02bb1-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="02bb1-132">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="02bb1-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="02bb1-133">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="02bb1-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
