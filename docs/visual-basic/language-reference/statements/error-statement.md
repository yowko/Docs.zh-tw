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
ms.openlocfilehash: 35ba1f19654d1d23ac1ec73564bc36b0af4f6777
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404741"
---
# <a name="error-statement"></a><span data-ttu-id="704b0-102">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="704b0-102">Error Statement</span></span>
<span data-ttu-id="704b0-103">模擬發生錯誤的次數。</span><span class="sxs-lookup"><span data-stu-id="704b0-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="704b0-104">語法</span><span class="sxs-lookup"><span data-stu-id="704b0-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="704b0-105">組件</span><span class="sxs-lookup"><span data-stu-id="704b0-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="704b0-106">必要。</span><span class="sxs-lookup"><span data-stu-id="704b0-106">Required.</span></span> <span data-ttu-id="704b0-107">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="704b0-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="704b0-108">備註</span><span class="sxs-lookup"><span data-stu-id="704b0-108">Remarks</span></span>  
 <span data-ttu-id="704b0-109">`Error`語句支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="704b0-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="704b0-110">在新程式碼中，尤其是在建立物件時，請使用 `Err` 物件的 `Raise` 方法來產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="704b0-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="704b0-111">如果已 `errornumber` 定義，則 `Error` 語句會在物件的屬性 `Err` 被指派下列預設值之後，呼叫錯誤處理常式：</span><span class="sxs-lookup"><span data-stu-id="704b0-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="704b0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="704b0-112">Property</span></span>|<span data-ttu-id="704b0-113">值</span><span class="sxs-lookup"><span data-stu-id="704b0-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="704b0-114">指定為語句之引數的值 `Error` 。</span><span class="sxs-lookup"><span data-stu-id="704b0-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="704b0-115">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="704b0-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="704b0-116">目前 Visual Basic 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="704b0-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="704b0-117">對應至指定之函式傳回值的字串運算式 `Error` `Number` （如果這個字串存在）。</span><span class="sxs-lookup"><span data-stu-id="704b0-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="704b0-118">如果字串不存在，則 `Description` 包含長度為零的字串（""）。</span><span class="sxs-lookup"><span data-stu-id="704b0-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="704b0-119">適當 Visual Basic 說明檔的完整磁片磁碟機、路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="704b0-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="704b0-120">適當的 Visual Basic 說明檔內容識別碼，用於對應于屬性的錯誤 `Number` 。</span><span class="sxs-lookup"><span data-stu-id="704b0-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="704b0-121">零個。</span><span class="sxs-lookup"><span data-stu-id="704b0-121">Zero.</span></span>|  
  
 <span data-ttu-id="704b0-122">如果沒有錯誤處理常式存在，或未啟用，則會建立錯誤訊息，並從 `Err` 物件屬性顯示。</span><span class="sxs-lookup"><span data-stu-id="704b0-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="704b0-123">某些 Visual Basic 主應用程式無法建立物件。</span><span class="sxs-lookup"><span data-stu-id="704b0-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="704b0-124">請參閱主機應用程式的檔，以判斷它是否可以建立類別和物件。</span><span class="sxs-lookup"><span data-stu-id="704b0-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="704b0-125">範例</span><span class="sxs-lookup"><span data-stu-id="704b0-125">Example</span></span>  
 <span data-ttu-id="704b0-126">這個範例會使用 `Error` 語句來產生錯誤號碼11。</span><span class="sxs-lookup"><span data-stu-id="704b0-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="704b0-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="704b0-127">Requirements</span></span>  
 <span data-ttu-id="704b0-128">**命名空間：** [Microsoft.](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="704b0-128">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="704b0-129">**元件：** Visual Basic 執行時間程式庫（在 Microsoft 中）</span><span class="sxs-lookup"><span data-stu-id="704b0-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704b0-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="704b0-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="704b0-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="704b0-131">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="704b0-132">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="704b0-132">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="704b0-133">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="704b0-133">Error Messages</span></span>](../error-messages/index.md)
