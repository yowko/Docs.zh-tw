---
title: "針對 LINQ to DataSet 進行偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 針對 LINQ to DataSet 進行偵錯
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 支援針對 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 程式碼進行偵錯。  不過，針對 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 程式碼和非 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Managed 程式碼進行偵錯有些不同。多數偵錯功能都使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 陳述式，包括步進、設定中斷點，以及檢視顯示在偵錯工具視窗中的結果。  但是，延後查詢執行在針對 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 程式碼進行偵錯時，有一些您必須考慮的副作用，而且在使用 \[編輯後繼續\] 時，有一些限制。  本主題討論 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] \(相較於非 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Managed 程式碼\) 專屬的偵錯觀點。  
  
## 檢視結果  
 您可以使用 DataTips、監看式視窗和快速監看式對話方塊檢視 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 陳述式的結果。  藉由使用來源視窗，您可以在來源視窗中暫停查詢的指標，而且 DataTip 將會出現。  您可以複製 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 變數，並將其貼入監看式視窗或快速監看式對話方塊中。在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 中建立或宣告查詢時，不會評估該查詢，只有在執行查詢時，才會進行評估。  這稱為「*延後執行*」。  因此，查詢變數在接受評估前沒有值。  如需詳細資訊，請參閱[LINQ to DataSet 中的查詢](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)。  
  
 偵錯工具必須評估查詢，才能顯示查詢結果。  當您在偵錯工具中檢視 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢結果時，會發生這個隱含的評估，而且該評估會產生一些您應該考慮的效果。  每個查詢評估會耗費些許時間。  展開結果節點也會耗用時間。  對於某些查詢而言，重複的評估可能會造成明顯的效能影響。  評估查詢也可能造成變更資料值與程式狀態的副作用。  並不是所有的查詢都有副作用。  若要判斷查詢是否可以安全地接受評估而沒有副作用，您必須了解實作查詢的程式碼。  如需詳細資訊，請參閱[副作用和運算式](../Topic/Side%20Effects%20and%20Expressions.md)。  
  
## 編輯後繼續  
 \[編輯後繼續\] 不支援 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢的變更。  如果您在偵錯工作階段期間加入、移除或變更 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 陳述式，會出現一個對話方塊，告訴您 \[編輯後繼續\] 不支援變更。  此時，您可以復原變更，或者是停止偵錯工作階段並使用編輯過的程式碼重新啟動新的工作階段。  
  
 此外，\[編輯後繼續\] 不支援變更用於 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 陳述式之變數的型別或值。  同樣地，您可以復原變更，或者是停止並重新啟動偵錯工作階段。  
  
 在 Visual Studio 的 Visual C\# 中，您無法利用包含 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢的方法，在任何程式碼上使用 \[編輯後繼續\]。  
  
 在 Visual Studio 的 Visual C\# 中，您甚至可以利用包含 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢的方法，在非 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 程式碼上使用 \[編輯後繼續\]。  即使變更會影響 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢的行號，您還是可以加入或移除 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 陳述式前的程式碼。  您對於非 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 程式碼的 Visual Basic 偵錯經驗與 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 推出前相同。  不過，您無法變更、加入或移除 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢，除非您停止偵錯，才能套用變更。  
  
## 請參閱  
 [偵錯 Managed 程式碼](../Topic/Debugging%20Managed%20Code.md)   
 [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)