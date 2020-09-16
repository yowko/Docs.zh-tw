---
title: 偵錯 LINQ to DataSet 查詢
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 5f6e711d13a71f73a75e774c9251c5c29216b860
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554344"
---
# <a name="debugging-linq-to-dataset-queries"></a>偵錯 LINQ to DataSet 查詢

Visual Studio 支援 LINQ to DataSet 程式碼的偵錯工具。 不過，LINQ to DataSet 程式碼和非 LINQ to DataSet managed 程式碼的偵錯工具之間有一些差異。 大部分的偵錯工具都可搭配 LINQ to DataSet 的語句使用，包括逐步執行、設定中斷點，以及顯示在偵錯工具視窗中的結果。 但是，中的延遲查詢執行有一些副作用，您應該考慮在 LINQ to DataSet 程式碼進行偵錯工具時，使用 [編輯後繼續] 有一些限制。 本主題將討論與非 LINQ to DataSet managed 程式碼相較之下，LINQ to DataSet 特有的偵錯工具層面。  
  
## <a name="viewing-results"></a>檢視結果  
 您可以使用 [資料提示]、[監看式視窗] 和 [快速監看式] 對話方塊來查看 LINQ to DataSet 語句的結果。 藉由使用來源視窗，您可以在來源視窗中暫停查詢的指標，而且 DataTip 將會出現。 您可以複製 LINQ to DataSet 變數，並將它貼到監看式視窗或 [快速監看式] 對話方塊中。 在 LINQ to DataSet 中，在建立或宣告查詢時，不會評估該查詢，但只有在執行查詢時才會進行評估。 這稱為「 *延後執行*」。 因此，查詢變數在接受評估前沒有值。 如需詳細資訊，請參閱 [LINQ to DataSet 中的查詢](queries-in-linq-to-dataset.md)。  
  
 偵錯工具必須評估查詢，才能顯示查詢結果。 當您在偵錯工具中查看 LINQ to DataSet 查詢結果時，就會發生這種隱含的評估，且您應該考慮一些效果。 每個查詢評估會耗費些許時間。 展開結果節點也會耗用時間。 對於某些查詢而言，重複的評估可能會造成明顯的效能影響。 評估查詢也可能造成變更資料值與程式狀態的副作用。 並不是所有的查詢都有副作用。 若要判斷查詢是否可以安全地接受評估而沒有副作用，您必須了解實作查詢的程式碼。 如需詳細資訊，請參閱 [副作用和運算式](/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120))。  
  
## <a name="edit-and-continue"></a>編輯後繼續  
 [編輯後繼續] 不支援 LINQ to DataSet 查詢的變更。 如果您在偵錯工具期間加入、移除或變更 LINQ to DataSet 語句，會出現一個對話方塊，告訴您 [編輯後繼續] 不支援變更。 此時，您可以復原變更，或者是停止偵錯工作階段並使用編輯過的程式碼重新啟動新的工作階段。  
  
 此外，[編輯後繼續] 不支援變更 LINQ to DataSet 語句中所使用之變數的類型或值。 同樣地，您可以復原變更，或者是停止並重新啟動偵錯工作階段。  
  
 在 Visual Studio 中的 Visual c # 中，您無法在包含 LINQ to DataSet 查詢之方法中的任何程式碼上使用 [編輯後繼續]。  
  
 在 Visual Studio 的 Visual Basic 中，您可以在非 LINQ to DataSet 的程式碼上使用 [編輯後繼續]，即使是在包含 LINQ to DataSet 查詢的方法中也一樣。 您可以在 LINQ to DataSet 語句之前新增或移除程式碼，即使這些變更會影響 LINQ to DataSet 查詢的行號。 您 Visual Basic 非 LINQ to DataSet 程式碼的偵錯工具體驗，與引進 LINQ to DataSet 之前保持不變。 不過，您無法變更、新增或移除 LINQ to DataSet 查詢，除非您停止調試以套用變更。  
  
## <a name="see-also"></a>另請參閱

- [偵錯 Managed 程式碼](/visualstudio/debugger/debugging-managed-code)
- [程式設計指南](programming-guide-linq-to-dataset.md)
