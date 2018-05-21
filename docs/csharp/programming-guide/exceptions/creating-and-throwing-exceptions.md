---
title: 建立和擲回例外狀況 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: 91676830d88ddee79c72211ab43b7be32fa8724e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a><span data-ttu-id="c105d-102">建立和擲回例外狀況 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c105d-102">Creating and Throwing Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="c105d-103">例外狀況是用來表示執行程式時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c105d-103">Exceptions are used to indicate that an error has occurred while running the program.</span></span> <span data-ttu-id="c105d-104">建立描述錯誤的例外狀況物件，然後使用 [throw](../../../csharp/language-reference/keywords/throw.md) 關鍵字「擲回」。</span><span class="sxs-lookup"><span data-stu-id="c105d-104">Exception objects that describe an error are created and then *thrown* with the [throw](../../../csharp/language-reference/keywords/throw.md) keyword.</span></span> <span data-ttu-id="c105d-105">執行階段接著會搜尋最相容的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="c105d-105">The runtime then searches for the most compatible exception handler.</span></span>  
  
 <span data-ttu-id="c105d-106">符合下列其中一或多個條件時，程式設計人員應該會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="c105d-106">Programmers should throw exceptions when one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="c105d-107">此方法無法完成其定義的功能。</span><span class="sxs-lookup"><span data-stu-id="c105d-107">The method cannot complete its defined functionality.</span></span>  
  
     <span data-ttu-id="c105d-108">例如，如果方法的參數具有無效值︰</span><span class="sxs-lookup"><span data-stu-id="c105d-108">For example, if a parameter to a method has an invalid value:</span></span>  
  
     [!code-csharp[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   <span data-ttu-id="c105d-109">根據物件狀態，對物件進行不適當的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c105d-109">An inappropriate call to an object is made, based on the object state.</span></span>  
  
     <span data-ttu-id="c105d-110">其中一個範例可能會嘗試寫入至唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="c105d-110">One example might be trying to write to a read-only file.</span></span> <span data-ttu-id="c105d-111">如果物件狀態不允許作業，則會根據這個類別的衍生來擲回 <xref:System.InvalidOperationException> 執行個體或物件。</span><span class="sxs-lookup"><span data-stu-id="c105d-111">In cases where an object state does not allow an operation, throw an instance of <xref:System.InvalidOperationException> or an object based on a derivation of this class.</span></span> <span data-ttu-id="c105d-112">這是擲回 <xref:System.InvalidOperationException> 物件的方法範例：</span><span class="sxs-lookup"><span data-stu-id="c105d-112">This is an example of a method that throws an <xref:System.InvalidOperationException> object:</span></span>  
  
     [!code-csharp[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   <span data-ttu-id="c105d-113">方法的引數造成例外狀況時。</span><span class="sxs-lookup"><span data-stu-id="c105d-113">When an argument to a method causes an exception.</span></span>  
  
     <span data-ttu-id="c105d-114">在此情況下，應該會攔截到原始例外狀況，並且應該會建立 <xref:System.ArgumentException> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c105d-114">In this case, the original exception should be caught and an <xref:System.ArgumentException> instance should be created.</span></span> <span data-ttu-id="c105d-115">應該將原始例外狀況傳遞至 <xref:System.ArgumentException> 的建構函式，作為 <xref:System.Exception.InnerException%2A> 參數：</span><span class="sxs-lookup"><span data-stu-id="c105d-115">The original exception should be passed to the constructor of the <xref:System.ArgumentException> as the <xref:System.Exception.InnerException%2A> parameter:</span></span>  
  
     [!code-csharp[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 <span data-ttu-id="c105d-116">例外狀況包含名為 <xref:System.Exception.StackTrace%2A> 的屬性。</span><span class="sxs-lookup"><span data-stu-id="c105d-116">Exceptions contain a property named <xref:System.Exception.StackTrace%2A>.</span></span> <span data-ttu-id="c105d-117">這個字串包含目前呼叫堆疊上的方法名稱，以及擲回每個方法之例外狀況的檔案名稱和行號。</span><span class="sxs-lookup"><span data-stu-id="c105d-117">This string contains the name of the methods on the current call stack, together with the file name and line number where the exception was thrown for each method.</span></span> <span data-ttu-id="c105d-118">Common Language Runtime (CLR) 會從 `throw` 陳述式的位置自動建立 <xref:System.Exception.StackTrace%2A> 物件，因此必須從堆疊追蹤應該開始的位置擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c105d-118">A <xref:System.Exception.StackTrace%2A> object is created automatically by the common language runtime (CLR) from the point of the `throw` statement, so that exceptions must be thrown from the point where the stack trace should begin.</span></span>  
  
 <span data-ttu-id="c105d-119">所有例外狀況包含名為 <xref:System.Exception.Message%2A> 的屬性。</span><span class="sxs-lookup"><span data-stu-id="c105d-119">All exceptions contain a property named <xref:System.Exception.Message%2A>.</span></span> <span data-ttu-id="c105d-120">此字串應該設為說明例外狀況的原因。</span><span class="sxs-lookup"><span data-stu-id="c105d-120">This string should be set to explain the reason for the exception.</span></span> <span data-ttu-id="c105d-121">請注意，安全性敏感資訊不應該放在訊息文字中。</span><span class="sxs-lookup"><span data-stu-id="c105d-121">Note that information that is sensitive to security should not be put in the message text.</span></span> <span data-ttu-id="c105d-122">除了 <xref:System.Exception.Message%2A> 之外，<xref:System.ArgumentException> 還會包含一個名為 <xref:System.ArgumentException.ParamName%2A> 的屬性，該屬性應設定為導致擲回例外狀況的引數名稱。</span><span class="sxs-lookup"><span data-stu-id="c105d-122">In addition to <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contains a property named <xref:System.ArgumentException.ParamName%2A> that should be set to the name of the argument that caused the exception to be thrown.</span></span> <span data-ttu-id="c105d-123">如果是屬性 setter，則 <xref:System.ArgumentException.ParamName%2A> 應設定為 `value`。</span><span class="sxs-lookup"><span data-stu-id="c105d-123">In the case of a property setter, <xref:System.ArgumentException.ParamName%2A> should be set to `value`.</span></span>  
  
 <span data-ttu-id="c105d-124">只要 public 和 protected 方法成員無法完成其預期函式，應該就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c105d-124">Public and protected methods members should throw exceptions whenever they cannot complete their intended functions.</span></span> <span data-ttu-id="c105d-125">擲回的例外狀況類別應該是可符合錯誤狀況的最特定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c105d-125">The exception class that is thrown should be the most specific exception available that fits the error conditions.</span></span> <span data-ttu-id="c105d-126">這些例外狀況應該記錄為類別功能的一部分，而且原始類別的衍生類別或更新應該會保留相同的行為，以進行回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="c105d-126">These exceptions should be documented as part of the class functionality, and derived classes or updates to the original class should retain the same behavior for backward compatibility.</span></span>  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a><span data-ttu-id="c105d-127">要在擲回例外狀況時避免的事項</span><span class="sxs-lookup"><span data-stu-id="c105d-127">Things to Avoid When Throwing Exceptions</span></span>  
 <span data-ttu-id="c105d-128">下列清單識別要在擲回例外狀況時避免的做法︰</span><span class="sxs-lookup"><span data-stu-id="c105d-128">The following list identifies practices to avoid when throwing exceptions:</span></span>  
  
-   <span data-ttu-id="c105d-129">例外狀況不應該用來在一般執行期間變更程式流程。</span><span class="sxs-lookup"><span data-stu-id="c105d-129">Exceptions should not be used to change the flow of a program as part of ordinary execution.</span></span> <span data-ttu-id="c105d-130">例外狀況只應該用來報告和處理錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="c105d-130">Exceptions should only be used to report and handle error conditions.</span></span>  
  
-   <span data-ttu-id="c105d-131">例外狀況不應該傳回為傳回值或參數，而不是擲回。</span><span class="sxs-lookup"><span data-stu-id="c105d-131">Exceptions should not be returned as a return value or parameter instead of being thrown.</span></span>  
  
-   <span data-ttu-id="c105d-132">請不要從您自己的原始程式碼刻意擲回 <xref:System.Exception?displayProperty=nameWithType>、<xref:System.SystemException?displayProperty=nameWithType>、<xref:System.NullReferenceException?displayProperty=nameWithType> 或 <xref:System.IndexOutOfRangeException?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c105d-132">Do not throw <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>, or <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> intentionally from your own source code.</span></span>  
  
-   <span data-ttu-id="c105d-133">請不要建立可在偵錯模式中擲回的例外狀況，而不是釋放模式。</span><span class="sxs-lookup"><span data-stu-id="c105d-133">Do not create exceptions that can be thrown in debug mode but not release mode.</span></span> <span data-ttu-id="c105d-134">若要在開發階段期間識別執行階段錯誤，請改用「偵錯判斷提示」。</span><span class="sxs-lookup"><span data-stu-id="c105d-134">To identify run-time errors during the development phase, use Debug Assert instead.</span></span>  
  
## <a name="defining-exception-classes"></a><span data-ttu-id="c105d-135">定義例外狀況類別</span><span class="sxs-lookup"><span data-stu-id="c105d-135">Defining Exception Classes</span></span>  
 <span data-ttu-id="c105d-136">程式可以擲回 <xref:System> 命名空間中預先定義的例外狀況類別 (但先前註明的項目除外)，或藉由衍生自 <xref:System.Exception> 來建立自己的例外狀況類別。</span><span class="sxs-lookup"><span data-stu-id="c105d-136">Programs can throw a predefined exception class in the <xref:System> namespace (except where previously noted), or create their own exception classes by deriving from <xref:System.Exception>.</span></span> <span data-ttu-id="c105d-137">衍生類別應該定義至少四個建構函式︰一個預設建構函式、一個設定訊息屬性的建構函式，以及同時設定 <xref:System.Exception.Message%2A> 和 <xref:System.Exception.InnerException%2A> 屬性的建構函式。</span><span class="sxs-lookup"><span data-stu-id="c105d-137">The derived classes should define at least four constructors: one default constructor, one that sets the message property, and one that sets both the <xref:System.Exception.Message%2A> and <xref:System.Exception.InnerException%2A> properties.</span></span> <span data-ttu-id="c105d-138">第四個建構函式是用來序列化例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c105d-138">The fourth constructor is used to serialize the exception.</span></span> <span data-ttu-id="c105d-139">新的例外狀況類別應為可序列化。</span><span class="sxs-lookup"><span data-stu-id="c105d-139">New exception classes should be serializable.</span></span> <span data-ttu-id="c105d-140">例如: </span><span class="sxs-lookup"><span data-stu-id="c105d-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 <span data-ttu-id="c105d-141">新屬性所提供的資料可用來解決例外狀況時，則只應該將新屬性新增至例外狀況類別。</span><span class="sxs-lookup"><span data-stu-id="c105d-141">New properties should only be added to the exception class when the data they provide is useful to resolving the exception.</span></span> <span data-ttu-id="c105d-142">如果將新屬性新增至衍生例外狀況類別，則應該覆寫 `ToString()` 來傳回已新增的資訊。</span><span class="sxs-lookup"><span data-stu-id="c105d-142">If new properties are added to the derived exception class, `ToString()` should be overridden to return the added information.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c105d-143">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c105d-143">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c105d-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="c105d-144">See Also</span></span>  
 [<span data-ttu-id="c105d-145">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c105d-145">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c105d-146">例外狀況和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="c105d-146">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="c105d-147">例外狀況階層架構</span><span class="sxs-lookup"><span data-stu-id="c105d-147">Exception Hierarchy</span></span>](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)  
 [<span data-ttu-id="c105d-148">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="c105d-148">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)
