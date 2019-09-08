---
title: 偵錯 LINQ to DataSet 查詢
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: a82fd3e99a556daf40e5c65a16cf20278f38ea26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785206"
---
# <a name="debugging-linq-to-dataset-queries"></a>偵錯 LINQ to DataSet 查詢

Visual Studio 支援 LINQ to DataSet 程式碼的偵錯工具。 不過，LINQ to DataSet 程式碼和非 LINQ to DataSet managed 程式碼的偵錯工具之間有一些差異。 大部分的偵錯工具功能都能與 LINQ to DataSet 語句搭配使用，包括逐步執行、設定中斷點，以及查看偵錯工具視窗中顯示的結果。 不過，中的延後查詢執行有一些副作用，您可以在對 LINQ to DataSet 程式碼進行偵錯工具時考慮，而且使用 [編輯後繼續] 會有一些限制。 本主題討論與非 LINQ to DataSet managed 程式碼相較之下，LINQ to DataSet 唯一的調試層面。  
  
## <a name="viewing-results"></a>檢視結果  
 您可以使用資料提示、監看式視窗和 [快速監看式] 對話方塊來查看 LINQ to DataSet 語句的結果。 藉由使用來源視窗，您可以在來源視窗中暫停查詢的指標，而且 DataTip 將會出現。 您可以複製 LINQ to DataSet 變數，並將它貼入監看式視窗或 [快速監看式] 對話方塊中。 在 LINQ to DataSet 中，不會在建立或宣告查詢時進行評估，而只會在執行查詢時進行評估。 這稱為「*延後執行*」。 因此，查詢變數在接受評估前沒有值。 如需詳細資訊，請參閱[LINQ to DataSet 中的查詢](queries-in-linq-to-dataset.md)。  
  
 偵錯工具必須評估查詢，才能顯示查詢結果。 當您在偵錯工具中查看 LINQ to DataSet 查詢結果時，就會發生這個隱含評估，而且它有一些您應該考慮的效果。 每個查詢評估會耗費些許時間。 展開結果節點也會耗用時間。 對於某些查詢而言，重複的評估可能會造成明顯的效能影響。 評估查詢也可能造成變更資料值與程式狀態的副作用。 並不是所有的查詢都有副作用。 若要判斷是否可以安全地評估查詢，而不會產生副作用，您必須瞭解執行查詢的程式碼。 如需詳細資訊，請參閱[副作用和運算式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120))。  
  
## <a name="edit-and-continue"></a>編輯後繼續  
 [編輯後繼續] 不支援變更 LINQ to DataSet 查詢。 如果您在偵錯工具期間加入、移除或變更 LINQ to DataSet 語句，就會出現對話方塊，告訴您 [編輯後繼續] 不支援變更。 此時，您可以復原變更，或者是停止偵錯工作階段並使用編輯過的程式碼重新啟動新的工作階段。  
  
 此外，[編輯後繼續] 不支援變更 LINQ to DataSet 語句中使用之變數的類型或值。 同樣地，您可以復原變更，或者是停止並重新啟動偵錯工作階段。  
  
 在 Visual Studio C#的 Visual 中，您無法在包含 LINQ to DataSet 查詢的方法中的任何程式碼上使用 [編輯後繼續]。  
  
 在 Visual Studio 的 Visual Basic 中，您可以在非 LINQ to DataSet 的程式碼上使用 [編輯後繼續]，即使是在包含 LINQ to DataSet 查詢的方法中也一樣。 您可以在 LINQ to DataSet 語句之前加入或移除程式碼，即使變更會影響 LINQ to DataSet 查詢的行號也一樣。 非 LINQ to DataSet 程式碼的 Visual Basic 偵測體驗，與引進 LINQ to DataSet 之前相同。 不過，您無法變更、加入或移除 LINQ to DataSet 查詢，除非您停止進行調試，才能套用變更。  
  
## <a name="see-also"></a>另請參閱

- [偵錯 Managed 程式碼](/visualstudio/debugger/debugging-managed-code)
- [程式設計手冊](programming-guide-linq-to-dataset.md)
