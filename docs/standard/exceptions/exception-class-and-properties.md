---
title: Exception 類別和屬性
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cdc464234871fc07feeeb8dd02635ebdd151d76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="exception-class-and-properties"></a><span data-ttu-id="326a0-102">Exception 類別和屬性</span><span class="sxs-lookup"><span data-stu-id="326a0-102">Exception class and properties</span></span>

<span data-ttu-id="326a0-103"><xref:System.Exception> 類別是例外狀況所繼承的基底類別。</span><span class="sxs-lookup"><span data-stu-id="326a0-103">The <xref:System.Exception> class is the base class from which exceptions inherit.</span></span> <span data-ttu-id="326a0-104">例如 <xref:System.InvalidCastException> 類別的階層如下：</span><span class="sxs-lookup"><span data-stu-id="326a0-104">For example, the <xref:System.InvalidCastException> class hierarchy is as follows:</span></span>

```
Object
  Exception
    SystemException
       InvalidCastException
```

<span data-ttu-id="326a0-105"><xref:System.Exception> 類別具有下列屬性，讓您更容易了解例外狀況。</span><span class="sxs-lookup"><span data-stu-id="326a0-105">The <xref:System.Exception> class has the following properties that help make understanding an exception easier.</span></span>

| <span data-ttu-id="326a0-106">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="326a0-106">Property Name</span></span> | <span data-ttu-id="326a0-107">描述</span><span class="sxs-lookup"><span data-stu-id="326a0-107">Description</span></span> |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <span data-ttu-id="326a0-108"><xref:System.Collections.IDictionary> 會將任意資料保存在索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="326a0-108">An <xref:System.Collections.IDictionary> that holds arbitrary data in key-value pairs.</span></span> |
| <xref:System.Exception.HelpLink> | <span data-ttu-id="326a0-109">可保留說明檔的 URL (或 URN)，以提供有關例外狀況原因的廣泛資訊。</span><span class="sxs-lookup"><span data-stu-id="326a0-109">Can hold a URL (or URN) to a help file that provides extensive information about the cause of an exception.</span></span> |
| <xref:System.Exception.InnerException> | <span data-ttu-id="326a0-110">您可以在例外狀況處理期間，使用此屬性來建立及保留一系列的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="326a0-110">This property can be used to create and preserve a series of exceptions during exception handling.</span></span> <span data-ttu-id="326a0-111">您可以使用此屬性來建立新的例外狀況，其中包含先前攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="326a0-111">You can use it to create a new exception that contains previously caught exceptions.</span></span> <span data-ttu-id="326a0-112"><xref:System.Exception.InnerException> 屬性中的第二個例外狀況可以擷取原始的例外狀況，讓程式碼可以處理第二個例外狀況，以檢視其他額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="326a0-112">The original exception can be captured by the second exception in the <xref:System.Exception.InnerException> property, allowing code that handles the second exception to examine the additional information.</span></span> <span data-ttu-id="326a0-113">例如，假設您有一個方法會接收格式不正確的引數。</span><span class="sxs-lookup"><span data-stu-id="326a0-113">For example, suppose you have a method that receives an argument that's improperly formatted.</span></span>  <span data-ttu-id="326a0-114">此程式碼會嘗試讀取引數，但擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="326a0-114">The code tries to read the argument, but an exception is thrown.</span></span> <span data-ttu-id="326a0-115">此方法會攔截例外狀況並擲回 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="326a0-115">The method catches the exception and throws a <xref:System.FormatException>.</span></span> <span data-ttu-id="326a0-116">為了改善呼叫端判斷所擲回例外狀況原因的能力，有時需要讓方法攔截 Helper 常式所擲回的例外狀況，再擲回更清楚指出所發生錯誤的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="326a0-116">To improve the caller's ability to determine the reason an exception is thrown, it is sometimes desirable for a method to catch an exception thrown by a helper routine and then throw an exception more indicative of the error that has occurred.</span></span> <span data-ttu-id="326a0-117">您可以建立全新且更有意義的例外狀況，其中的內部例外狀況參考可設定為原始例外狀況。</span><span class="sxs-lookup"><span data-stu-id="326a0-117">A new and more meaningful exception can be created, where the inner exception reference can be set to the original exception.</span></span> <span data-ttu-id="326a0-118">這個更有意義的例外狀況接著會擲回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="326a0-118">This more meaningful exception can then be thrown to the caller.</span></span> <span data-ttu-id="326a0-119">請注意，透過這項功能，您可以建立一系列的連結例外狀況，每個例外狀況後面接著先前擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="326a0-119">Note that with this functionality, you can create a series of linked exceptions that ends with the exception that was thrown first.</span></span> |
| <xref:System.Exception.Message> | <span data-ttu-id="326a0-120">提供有關例外狀況原因的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="326a0-120">Provides details about the cause of an exception.</span></span>
| <xref:System.Exception.Source> | <span data-ttu-id="326a0-121">取得或設定造成錯誤的應用程式或物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="326a0-121">Gets or sets the name of the application or the object that causes the error.</span></span> |
| <xref:System.Exception.StackTrace>| <span data-ttu-id="326a0-122">包含可用來判斷發生錯誤位置的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="326a0-122">Contains a stack trace that can be used to determine where an error occurred.</span></span> <span data-ttu-id="326a0-123">堆疊追蹤包括原始程式檔名稱和程式行號 (若有偵錯資訊的話)。</span><span class="sxs-lookup"><span data-stu-id="326a0-123">The stack trace includes the source file name and program line number if debugging information is available.</span></span> |

<span data-ttu-id="326a0-124">大部分繼承自 <xref:System.Exception> 的類別不會實作其他成員或提供其他功能；它們只會繼承自 <xref:System.Exception>。</span><span class="sxs-lookup"><span data-stu-id="326a0-124">Most of the classes that inherit from <xref:System.Exception> do not implement additional members or provide additional functionality; they simply inherit from <xref:System.Exception>.</span></span> <span data-ttu-id="326a0-125">因此，您可以在例外狀況類別階層架構、例外狀況名稱和例外狀況所包含的資訊中，找到例外狀況的最重要資訊。</span><span class="sxs-lookup"><span data-stu-id="326a0-125">Therefore, the most important information for an exception can be found in the hierarchy of exception classes, the exception name, and the information contained in the exception.</span></span>

<span data-ttu-id="326a0-126">建議只擲回及攔截衍生自 <xref:System.Exception> 的物件，但您可以擲回任何衍生自 <xref:System.Object> 類別的物件作為例外狀況。</span><span class="sxs-lookup"><span data-stu-id="326a0-126">We recommend that you throw and catch only objects that derive from <xref:System.Exception>, but you can throw any object that derives from the <xref:System.Object> class as an exception.</span></span> <span data-ttu-id="326a0-127">請注意，並非所有語言都能擲回及攔截不是衍生自 <xref:System.Exception> 的物件。</span><span class="sxs-lookup"><span data-stu-id="326a0-127">Note that not all languages support throwing and catching objects that do not derive from <xref:System.Exception>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="326a0-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="326a0-128">See Also</span></span>  
[<span data-ttu-id="326a0-129">例外狀況</span><span class="sxs-lookup"><span data-stu-id="326a0-129">Exceptions</span></span>](index.md)
