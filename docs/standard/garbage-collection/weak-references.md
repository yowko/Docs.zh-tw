---
title: 弱式參考
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03da36090c255f635036a9bd518bdacd99404ed4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="weak-references"></a>弱式參考
在應用程式碼可以存取使用中物件時，記憶體回收行程無法透過應用程式回收該物件。 應用程式即具有物件的強式參考。  
  
 弱式參考允許記憶體回收行程回收物件，同時仍然允許應用程式存取物件。 沒有強式參考時，除非回收物件，否則弱式參考僅在時間量不定期間才有效。 當您使用弱式參考時，應用程式仍然可以取得物件的強式參考，以防止回收該物件。 不過，記憶體回收行程在重新建立強式參考之前之前先取得物件，一定有其風險。  
  
 弱式參考適用於使用大量記憶體的物件，但可以在透過記憶體回收對其進行回收時輕鬆地予以重建。  
  
 假設 Windows Forms 應用程式中的樹狀檢視會向使用者顯示複雜的階層式選項。 如果基礎資料很大，則使用者參與應用程式中的其他作業時，將樹狀結構保留在記憶體不具效率。  
  
 當使用者切換到應用程式的另一個部分時，您可以使用 <xref:System.WeakReference> 類別來建立樹狀結構的弱式參考，並終結所有強式參考。 使用者切換回樹狀結構時，應用程式會嘗試取得樹狀結構的強式參考，如果成功，可以避免重新建構樹狀結構。  
  
 若要建立物件的弱式參考，請使用要追蹤之物件的執行個體來建立 <xref:System.WeakReference>。 接著將 <xref:System.WeakReference.Target%2A> 屬性設定為該物件，並將物件的原始參考設定為 `null`。 如需程式碼範例，請參閱類別庫中的 <xref:System.WeakReference>。  
  
## <a name="short-and-long-weak-references"></a>簡短和完整弱式參考  
 您可以建立簡短弱式參考或完整弱式參考︰  
  
-   Short  
  
     透過記憶體回收回收物件時，簡短弱式參考的目標會變成 `null`。 弱式參考本身是 Managed 物件，而且很容易進行記憶體回收，就像任何其他 Managed 物件一樣。  簡短弱式參考是 <xref:System.WeakReference> 的預設建構函式。  
  
-   Long  
  
     在呼叫物件的 <xref:System.Object.Finalize%2A> 方法之後，會保留完整弱式參考。 這樣會重建物件，但是物件的狀態仍然無法預測。 若要使用完整參考，請在 <xref:System.WeakReference> 建構函式中指定 `true`。  
  
     如果物件的類型沒有 <xref:System.Object.Finalize%2A> 方法，則會套用簡短的弱式參考功能，而且弱式參考只在回收目標之前有效，而目標的回收可以在執行完成項之後隨時執行。  
  
 若要建立強式參考，並再次使用物件，請將 <xref:System.WeakReference> 的 <xref:System.WeakReference.Target%2A> 屬性轉換為物件的類型。 如果 <xref:System.WeakReference.Target%2A> 屬性傳回 `null`，則已回收物件；否則，您可以繼續使用物件，因為應用程式已重新取得其強式參考。  
  
## <a name="guidelines-for-using-weak-references"></a>使用弱式參考的指導方針  
 只在物件狀態於完成之後無法預期時，才會在必要時使用完整弱式參考。  
  
 請避免使用小型物件的弱式參考，因為指標本身可能一樣大或較大。  
  
 請避免使用弱式參考作為記憶體管理問題的自動解決方案。 相反地，開發有效的快取原則來處理您的應用程式物件。  
  
## <a name="see-also"></a>請參閱  
 [記憶體回收](../../../docs/standard/garbage-collection/index.md)
