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
ms.openlocfilehash: f3f9f5ecb96686fe525e98cf64672d81a3145796
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873278"
---
# <a name="error-statement"></a><span data-ttu-id="4814d-102">Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="4814d-102">Error Statement</span></span>

<span data-ttu-id="4814d-103">模擬錯誤的發生。</span><span class="sxs-lookup"><span data-stu-id="4814d-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4814d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4814d-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="4814d-105">組件</span><span class="sxs-lookup"><span data-stu-id="4814d-105">Parts</span></span>  

 `errornumber`  
 <span data-ttu-id="4814d-106">必要。</span><span class="sxs-lookup"><span data-stu-id="4814d-106">Required.</span></span> <span data-ttu-id="4814d-107">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="4814d-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4814d-108">備註</span><span class="sxs-lookup"><span data-stu-id="4814d-108">Remarks</span></span>  

 <span data-ttu-id="4814d-109">`Error`為了回溯相容性，支援語句。</span><span class="sxs-lookup"><span data-stu-id="4814d-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="4814d-110">在新的程式碼中，特別是在建立物件時，請使用 `Err` 物件的 `Raise` 方法來產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="4814d-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="4814d-111">如果已 `errornumber` 定義， `Error` 語句會在物件的屬性 `Err` 指派下列預設值之後，呼叫錯誤處理常式：</span><span class="sxs-lookup"><span data-stu-id="4814d-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="4814d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4814d-112">Property</span></span>|<span data-ttu-id="4814d-113">值</span><span class="sxs-lookup"><span data-stu-id="4814d-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="4814d-114">將值指定為語句的引數 `Error` 。</span><span class="sxs-lookup"><span data-stu-id="4814d-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="4814d-115">可以是任何有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="4814d-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="4814d-116">目前 Visual Basic 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="4814d-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="4814d-117">字串運算式，對應至指定之函數的傳回值 `Error` `Number` （如果這個字串存在的話）。</span><span class="sxs-lookup"><span data-stu-id="4814d-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="4814d-118">如果字串不存在，則會 `Description` 包含長度為零的字串 ( "" ) 。</span><span class="sxs-lookup"><span data-stu-id="4814d-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="4814d-119">適當的 Visual Basic 說明檔的完整磁片磁碟機、路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4814d-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="4814d-120">適當的 Visual Basic 說明檔內容識別碼，適用于對應于屬性的錯誤 `Number` 。</span><span class="sxs-lookup"><span data-stu-id="4814d-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="4814d-121">零個。</span><span class="sxs-lookup"><span data-stu-id="4814d-121">Zero.</span></span>|  
  
 <span data-ttu-id="4814d-122">如果沒有錯誤處理常式，或未啟用任何錯誤處理常式，則會從物件屬性建立並顯示錯誤訊息 `Err` 。</span><span class="sxs-lookup"><span data-stu-id="4814d-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4814d-123">某些 Visual Basic 主機應用程式無法建立物件。</span><span class="sxs-lookup"><span data-stu-id="4814d-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="4814d-124">請參閱主機應用程式的檔，以判斷它是否可以建立類別和物件。</span><span class="sxs-lookup"><span data-stu-id="4814d-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4814d-125">範例</span><span class="sxs-lookup"><span data-stu-id="4814d-125">Example</span></span>  

 <span data-ttu-id="4814d-126">這個範例會使用 `Error` 語句來產生錯誤號碼11。</span><span class="sxs-lookup"><span data-stu-id="4814d-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="4814d-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="4814d-127">Requirements</span></span>  

 <span data-ttu-id="4814d-128">**命名空間：** [Microsoft.](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="4814d-128">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="4814d-129">**元件：** Microsoft.VisualBasic.dll) 中的 Visual Basic 執行時間程式庫 (</span><span class="sxs-lookup"><span data-stu-id="4814d-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4814d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4814d-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="4814d-131">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="4814d-131">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="4814d-132">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="4814d-132">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="4814d-133">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="4814d-133">Error Messages</span></span>](../error-messages/index.md)
