---
title: 建立和擲回例外狀況 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: c7775de75ddbf274f3a1555c9f0daaf63bbee713
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235341"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>建立和擲回例外狀況 (C# 程式設計手冊)
例外狀況是用來表示執行程式時發生錯誤。 建立描述錯誤的例外狀況物件，然後使用 [throw](../../../csharp/language-reference/keywords/throw.md) 關鍵字「擲回」。 執行階段接著會搜尋最相容的例外狀況處理常式。  
  
 符合下列其中一或多個條件時，程式設計人員應該會擲回例外狀況：  
  
-   此方法無法完成其定義的功能。  
  
     例如，如果方法的參數具有無效值︰  
  
     [!code-csharp[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   根據物件狀態，對物件進行不適當的呼叫。  
  
     其中一個範例可能會嘗試寫入至唯讀檔案。 如果物件狀態不允許作業，則會根據這個類別的衍生來擲回 <xref:System.InvalidOperationException> 執行個體或物件。 這是擲回 <xref:System.InvalidOperationException> 物件的方法範例：  
  
     [!code-csharp[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   方法的引數造成例外狀況時。  
  
     在此情況下，應該會攔截到原始例外狀況，並且應該會建立 <xref:System.ArgumentException> 執行個體。 應該將原始例外狀況傳遞至 <xref:System.ArgumentException> 的建構函式，作為 <xref:System.Exception.InnerException%2A> 參數：  
  
     [!code-csharp[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 例外狀況包含名為 <xref:System.Exception.StackTrace%2A> 的屬性。 這個字串包含目前呼叫堆疊上的方法名稱，以及擲回每個方法之例外狀況的檔案名稱和行號。 Common Language Runtime (CLR) 會從 `throw` 陳述式的位置自動建立 <xref:System.Exception.StackTrace%2A> 物件，因此必須從堆疊追蹤應該開始的位置擲回例外狀況。  
  
 所有例外狀況包含名為 <xref:System.Exception.Message%2A> 的屬性。 此字串應該設為說明例外狀況的原因。 請注意，安全性敏感資訊不應該放在訊息文字中。 除了 <xref:System.Exception.Message%2A> 之外，<xref:System.ArgumentException> 還會包含一個名為 <xref:System.ArgumentException.ParamName%2A> 的屬性，該屬性應設定為導致擲回例外狀況的引數名稱。 如果是屬性 setter，則 <xref:System.ArgumentException.ParamName%2A> 應設定為 `value`。  
  
 只要 public 和 protected 方法無法完成其預期函式，應該就會擲回例外狀況。 擲回的例外狀況類別應該是可符合錯誤狀況的最特定例外狀況。 這些例外狀況應該記錄為類別功能的一部分，而且原始類別的衍生類別或更新應該會保留相同的行為，以進行回溯相容性。  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>要在擲回例外狀況時避免的事項  
 下列清單識別要在擲回例外狀況時避免的做法︰  
  
-   例外狀況不應該用來在一般執行期間變更程式流程。 例外狀況只應該用來報告和處理錯誤狀況。  
  
-   例外狀況不應該傳回為傳回值或參數，而不是擲回。  
  
-   請不要從您自己的原始程式碼刻意擲回 <xref:System.Exception?displayProperty=nameWithType>、<xref:System.SystemException?displayProperty=nameWithType>、<xref:System.NullReferenceException?displayProperty=nameWithType> 或 <xref:System.IndexOutOfRangeException?displayProperty=nameWithType>。  
  
-   請不要建立可在偵錯模式中擲回的例外狀況，而不是釋放模式。 若要在開發階段期間識別執行階段錯誤，請改用「偵錯判斷提示」。  
  
## <a name="defining-exception-classes"></a>定義例外狀況類別  
 程式可以擲回 <xref:System> 命名空間中預先定義的例外狀況類別 (但先前註明的項目除外)，或藉由衍生自 <xref:System.Exception> 來建立自己的例外狀況類別。 衍生類別應該定義至少四個建構函式︰一個預設建構函式、一個設定訊息屬性的建構函式，以及同時設定 <xref:System.Exception.Message%2A> 和 <xref:System.Exception.InnerException%2A> 屬性的建構函式。 第四個建構函式是用來序列化例外狀況。 新的例外狀況類別應為可序列化。 例如：  
  
 [!code-csharp[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 新屬性所提供的資料可用來解決例外狀況時，則只應該將新屬性新增至例外狀況類別。 如果將新屬性新增至衍生例外狀況類別，則應該覆寫 `ToString()` 來傳回已新增的資訊。  
  
## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)的[例外狀況](~/_csharplang/spec/exceptions.md)與 [throw 陳述式](~/_csharplang/spec/statements.md#the-throw-statement)。 語言規格是 C# 語法及用法的限定來源。
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/index.md)  
- [例外狀況階層架構](../../../standard/exceptions/index.md)  
- [例外狀況處理](../../../csharp/programming-guide/exceptions/exception-handling.md)
