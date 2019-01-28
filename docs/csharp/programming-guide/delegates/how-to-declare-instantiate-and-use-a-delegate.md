---
title: HOW TO：宣告、產生和使用委派 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 8ecbac4608cfd42aa099a0cd66d7d22241a93265
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557704"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>HOW TO：宣告、產生和使用委派 (C# 程式設計手冊)
在 C# 1.0 和更新版本中，宣告委派的方式如下列範例所示。  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C# 2.0 提供更簡單的方式來撰寫先前的宣告，如下列範例所示。  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 在 C# 2.0 和更新版本中，也可以使用匿名方法來宣告和初始化[委派](../../../csharp/language-reference/keywords/delegate.md)，如下列範例所示。  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 在 C# 3.0 和更新版本中，也可以使用 lambda 運算式來宣告委派並將它具現化，如下列範例所示。  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 如需詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
 下列範例說明如何宣告、具現化和使用委派。 `BookDB` 類別會封裝用來保留書籍資料的書店資料庫。 它會公開 `ProcessPaperbackBooks` 方法，此方法會尋找資料庫中的所有平裝書，並針對每本書呼叫委派。 所使用的 `delegate` 類型稱為 `ProcessBookDelegate`。 `Test` 類別會使用這個類別來列印平裝書的書名和平均價格。  
  
 使用委派，可在書店資料庫和用戶端程式碼之間建立良好的功能區隔。 用戶端程式碼不需要瞭解保存書籍的方式，或是書店程式碼尋找平裝書的方式。 書店程式碼不需要知道當它找到平裝書之後該如何處理它們。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a>穩固程式設計  
  
-   宣告委派。  
  
     下列陳述式會宣告新的委派類型。  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     每個委派類型都會描述引數的數目和類型，以及它可以封裝之方法的傳回值類型。 每當需要一組新的引數類型或傳回值類型時，就必須宣告新的委派類型。  
  
-   具現化委派。  
  
     宣告委派類型之後，就必須建立委派物件並將其關聯至特定的方法。 在上述範例中，您可以藉由將 `PrintTitle` 方法傳遞至 `ProcessPaperbackBooks` 方法來執行此動作，如下列範例所示：  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     這會建立與[靜態](../../../csharp/language-reference/keywords/static.md)方法 `Test.PrintTitle` 相關聯的新委派物件。 同樣地，也可傳遞 `totaller` 物件上的非靜態方法 `AddBookToTotal`，如下列範例所示：  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     在這兩種情況下，會將新的委派物件傳遞至 `ProcessPaperbackBooks` 方法。  
  
     建立委派之後，與其相關聯的方法絕對不會變更；委派物件是不可變的。  
  
-   呼叫委派。  
  
     建立委派物件之後，通常會將委派物件傳遞至其他將呼叫委派的程式碼。 委派物件的呼叫方法是，使用委派物件的名稱，後面接著要傳遞至委派且已加上括號的引數。 以下是委派呼叫的範例：  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     委派可以同步呼叫 (如此範例所示)，或使用 `BeginInvoke` 和 `EndInvoke` 方法以非同步方式呼叫。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [事件](../../../csharp/programming-guide/events/index.md)
- [委派](../../../csharp/programming-guide/delegates/index.md)
