---
title: 偵錯 LINQ to DataSet 查詢
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 636d42566275f042f82f939e160c7fec5f180e96
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825504"
---
# <a name="debugging-linq-to-dataset-queries"></a>偵錯 LINQ to DataSet 查詢

Visual Studio 支援的偵錯[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]程式碼。 不過，有一些偵錯之間的差異[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]程式碼和非-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] managed 程式碼。 大部分的偵錯功能搭配[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]陳述式，包括逐步執行、 設定中斷點，以及檢視偵錯工具視窗所示的結果。 但是，延後查詢執行中的有一些副作用，您應該考慮在偵錯時[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]程式碼，並有一些限制，若要使用 [編輯後繼續]。 本主題討論特有的偵錯觀點[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]相較於非[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]managed 程式碼。  
  
## <a name="viewing-results"></a>檢視結果  
 您可以檢視的結果[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]使用 DataTips、 監看式 視窗中和 [快速監看式] 對話方塊中的陳述式。 藉由使用來源視窗，您可以在來源視窗中暫停查詢的指標，而且 DataTip 將會出現。 您可以複製 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 變數，並將其貼入監看式視窗或快速監看式對話方塊中。 在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 中建立或宣告查詢時，不會評估該查詢，只有在執行查詢時，才會進行評估。 這就叫做*延後執行*。 因此，查詢變數在接受評估前沒有值。 如需詳細資訊，請參閱 < [LINQ to DataSet 中的查詢](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)。  
  
 偵錯工具必須評估查詢，才能顯示查詢結果。 當您檢視時，就會發生這個隱含評估[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]中偵錯工具，而且查詢結果有一些您應該考慮的效果。 每個查詢評估會耗費些許時間。 展開結果節點也會耗用時間。 對於某些查詢而言，重複的評估可能會造成明顯的效能影響。 評估查詢也可能造成變更資料值與程式狀態的副作用。 並不是所有的查詢都有副作用。 若要判斷是否可以沒有副作用安全地評估查詢，您必須了解實作查詢的程式碼。 如需詳細資訊，請參閱 <<c0> [ 副作用和運算式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120))。  
  
## <a name="edit-and-continue"></a>編輯後繼續  
 編輯後繼續不支援變更[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢。 如果您新增、 移除或變更[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]偵錯工作階段的陳述式，會出現一個對話方塊，告訴您的變更不支援編輯後繼續。 此時，您可以復原變更，或者是停止偵錯工作階段並使用編輯過的程式碼重新啟動新的工作階段。  
  
 此外，編輯後繼續 不支援變更類型或變數中所使用的值[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]陳述式。 同樣地，您可以復原變更，或者是停止並重新啟動偵錯工作階段。  
  
 在 Visual C# 在 Visual Studio 中，您無法使用 編輯後繼續的方法中，包含任何程式碼上[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢。  
  
 在 Visual Basic 在 Visual Studio 中，您可以使用 編輯後繼續非[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]程式碼，即使在包含方法[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢。 您可以新增或移除程式碼，再[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]陳述式，即使這些變更會影響的行號[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢。 Visual Basic 偵錯體驗，非[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]程式碼維持不變之前[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]引進。 您無法變更、 新增或移除[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]查詢，不過，除非您停止偵錯以套用所做的變更。  
  
## <a name="see-also"></a>另請參閱
- [偵錯 Managed 程式碼](/visualstudio/debugger/debugging-managed-code)
- [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
