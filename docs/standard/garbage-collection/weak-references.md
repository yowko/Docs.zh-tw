---
title: "Weak References | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "weak references, short"
  - "weak references, using"
  - "weak references, long"
  - "garbage collection, weak references"
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Weak References
當應用程式的程式碼可以聯繫該應用程式正在使用的物件時，記憶體回收行程便無法回收該物件。  此應用程式就會擁有此物件的強式參考。  
  
 弱式參考允許記憶體回收行程在回收物件的同時，讓應用程式仍然可以存取此物件。  當強式參考不存在時，弱式參考只有在回收該物件之前的不定期間內才有效。  當您使用弱式參考時，應用程式仍舊可以取得此物件的強式參考，以防止該物件被回收。  不過，其中仍舊有風險，因為記憶體回收行程有可能在重建強式參考之前先到達該物件。  
  
 弱式參考對於使用大量記憶體的物件非常有用，但是如果這些物件被記憶體回收行程收回，則可以輕鬆地重建。  
  
 假設在 Windows Form 應用程式內的樹狀檢視中，對使用者顯示複雜的階層式選項。  如果基礎資料的數量很龐大，則當使用者與應用程式內的其他項目有關時，在記憶體內保存此樹狀目錄是沒有效率的作法。  
  
 當使用者切換到應用程式的另一個部分時，您可以使用 <xref:System.WeakReference> 類別來建立此樹狀目錄的弱式參考，並終結所有強式參考。  當使用者切換回此樹狀目錄時，應用程式會嘗試取得此樹狀目錄的強式參考，而如果成功的話，則會避免重建此樹狀目錄。  
  
 若要建立具有物件的弱式參考，您可以使用要追蹤之物件的執行個體 \(Instance\) 建立 <xref:System.WeakReference>。  接著您可以設定 <xref:System.WeakReference.Target%2A> 屬性為該物件，並將物件原先的參考設定為 `null`。  如需程式碼範例，請參閱類別庫 \(Class Library\) 內的 <xref:System.WeakReference>。  
  
## 短整數和長整數的弱式參考  
 您可以建立短整數 \(Short\) 的弱式參考或是長整數 \(Long\) 的弱式參考：  
  
-   Short  
  
     當物件被記憶體回收行程收回時，短整數弱式參考的目標會變為 `null`。  弱式參考本身是一個 Managed 物件，並且受到記憶體回收行程的管制，就像其他任何 Managed 物件一樣。短整數的弱式參考是 <xref:System.WeakReference> 的預設建構函式。  
  
-   Long  
  
     當呼叫此物件的 <xref:System.Object.Finalize%2A> 方法後，會保留長整數的弱式參考。  如此可讓物件重建，而物件的狀態則仍然無法預測。  若要使用長整數的參考，請在 <xref:System.WeakReference> 建構函式內指定 `true`。  
  
     如果此物件的型別沒有 <xref:System.Object.Finalize%2A> 方法，則會套用短整數的弱式參考功能，而弱式參考只有在目標被回收之前才有效，完成項執行後的任何時間都可能會回收目標。  
  
 若要建立強式參考並再次使用此物件，請將 <xref:System.WeakReference> 的 <xref:System.WeakReference.Target%2A> 屬性轉換為此物件的型別。  如果 <xref:System.WeakReference.Target%2A> 屬性傳回 `null`，則物件會被回收，否則您便可以繼續使用此物件，因為應用程式已重新取得它的強式參考。  
  
## 使用弱式參考的方針  
 只有在必要時才使用長整數的弱式參考，因為此物件的狀態在最終化之後將會無法預測。  
  
 避免使用小型物件的弱式參考，因為該指標本身可能較大。  
  
 避免使用弱式參考當做記憶體管理問題的自動解決方案，  而是要開發一個有效的快取原則來處理應用程式的物件。  
  
## 請參閱  
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)