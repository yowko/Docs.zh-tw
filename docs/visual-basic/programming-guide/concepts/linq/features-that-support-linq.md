---
title: 支援 LINQ 的功能
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 15585cd8277b1a0df7e3b262db7c9b7a231b16fa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383426"
---
# <a name="visual-basic-features-that-support-linq"></a>支援 LINQ 的 Visual Basic 功能
「語言整合式查詢」（LINQ）是指支援直接在語言中查詢語法和其他語言結構的 Visual Basic 技術。 有了 LINQ，您就不需要學習新的語言來查詢外部資料源。 您可以使用 Visual Basic 來查詢關係資料庫、XML 存放區或物件中的資料。 將查詢功能整合到語言中，可讓編譯時間檢查語法錯誤和型別安全。 這項整合也可確保您已經知道在 Visual Basic 中撰寫豐富、多樣化查詢所需知道的大部分知識。  
  
 下列各節將說明支援 LINQ 的語言結構，以提供足夠的詳細資料，讓您能夠開始閱讀簡介檔、程式碼範例和範例應用程式。 您也可以按一下連結，尋找如何將語言功能結合在一起，以啟用語言整合式查詢的詳細說明。 一個不錯的起點是[逐步解說：在 Visual Basic 中撰寫查詢](walkthrough-writing-queries.md)。  
  
## <a name="query-expressions"></a>查詢運算式  
 Visual Basic 中的查詢運算式可以用類似 SQL 或 XQuery 的宣告式語法來表示。 在編譯時期，查詢語法會轉換成 LINQ 提供者的標準查詢運算子擴充方法的實作為方法呼叫。 應用程式會藉由使用語句來指定適當的命名空間，以控制哪些標準查詢運算子在範圍中 `Imports` 。 Visual Basic 查詢運算式的語法如下所示：  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 如需詳細資訊，請參閱[Visual Basic 中的 LINQ 簡介](../../language-features/linq/introduction-to-linq.md)。  
  
## <a name="implicitly-typed-variables"></a>隱含類型變數  
 您可以讓編譯器推斷並指派型別，而不是在宣告和初始化變數時明確指定型別。 這稱為*區欄位型別推斷*。  
  
 推斷其類型的變數是強型別，就像您明確指定型別的變數一樣。 區欄位型別推斷僅適用于您在方法主體內定義區域變數的情況。 如需詳細資訊，請參閱[Option 推斷語句](../../../language-reference/statements/option-infer-statement.md)和[區欄位型別推斷](../../language-features/variables/local-type-inference.md)。  
  
 下列範例說明區域型別推斷。 若要使用此範例，您必須將設 `Option Infer` 為 `On` 。  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 區欄位型別推斷也可以建立匿名型別，這會在本節稍後說明，而且對於 LINQ 查詢而言是必要的。  
  
 在下列 LINQ 範例中，如果是或，就會發生型別推斷 `Option Infer` `On` `Off` 。 如果 `Option Infer` 為 `Off` ，且 `Option Strict` 為，則會發生編譯時期錯誤 `On` 。  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>物件初始設定式  
 當您必須建立匿名型別來保存查詢的結果時，就會在查詢運算式中使用物件初始化運算式。 它們也可以用來初始化查詢以外的命名類型物件。 藉由使用物件初始化運算式，您可以在單一行中初始化物件，而不需要明確呼叫函式。 假設您有一個名為且 `Customer` 具有公用 `Name` 和屬性的類別 `Phone` ，以及其他屬性，則可以使用此方式來使用物件初始化運算式：  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 如需詳細資訊，請參閱[物件初始化運算式：名稱和匿名型別](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。  
  
## <a name="anonymous-types"></a>匿名類型  
 匿名型別提供一個方便的方式，將一組屬性暫時分組到您想要包含在查詢結果中的元素。 這可讓您依任何順序選取查詢中可用欄位的任意組合，而不需要定義專案的命名資料類型。  
  
 *匿名型*別是由編譯器動態地建造。 類型的名稱是由編譯器指派，而且可能會隨著每個新的編譯而變更。 因此，您無法直接使用此名稱。 匿名型別會以下列方式初始化：  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 如需詳細資訊，請參閱[匿名](../../language-features/objects-and-classes/anonymous-types.md)型別。  
  
## <a name="extension-methods"></a>擴充方法  
 擴充方法可讓您將方法加入至定義以外的資料類型或介面。 這項功能可讓您將新方法加入至現有的類型，而不需要實際修改類型。 標準查詢運算子本身是一組擴充方法，可為任何可執行檔型別提供 LINQ 查詢功能 <xref:System.Collections.Generic.IEnumerable%601> 。 <xref:System.Collections.Generic.IEnumerable%601>包含、和的其他延伸模組 <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Union%2A> <xref:System.Linq.Enumerable.Intersect%2A> 。  
  
 下列擴充方法會將 print 方法新增至 <xref:System.String> 類別。  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 方法會如同的一般實例方法一樣呼叫 <xref:System.String> ：  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 如需詳細資訊，請參閱[擴充方法](../../language-features/procedures/extension-methods.md)。  
  
## <a name="lambda-expressions"></a>Lambda 運算式  
 Lambda 運算式是沒有名稱的函式，會計算並傳回單一值。 不同于命名函數，可以同時定義和執行 lambda 運算式。 下列範例會顯示4。  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 您可以將 lambda 運算式定義指派給變數名稱，然後使用此名稱來呼叫函數。 下列範例也會顯示4。  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 在 LINQ 中，lambda 運算式的基礎是許多標準查詢運算子。 編譯器會建立 lambda 運算式來捕捉在基本查詢方法（例如 `Where` 、 `Select` 、 `Order By` 、 `Take While` 和其他）中定義的計算。  
  
 例如，下列程式碼會定義一個查詢，以傳回一份學生清單中的所有資深學生。  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 查詢定義會編譯成類似下列範例的程式碼，其使用兩個 lambda 運算式來指定和的引數 `Where` `Select` 。  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 任一版本都可以使用迴圈來執行 `For Each` ：  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 如需詳細資訊，請參閱[Lambda 運算式](../../language-features/procedures/lambda-expressions.md)。  
  
## <a name="see-also"></a>另請參閱

- [Language-Integrated Query (LINQ) (Visual Basic)](index.md)
- [使用 Visual Basic 撰寫 LINQ 入門](getting-started-with-linq.md)
- [LINQ 與字串 (Visual Basic)](linq-and-strings.md)
- [Option Infer 陳述式](../../../language-reference/statements/option-infer-statement.md)
- [Long](../../../language-reference/statements/option-strict-statement.md)
