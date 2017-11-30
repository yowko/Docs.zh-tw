---
title: "弱式參考"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a>弱式參考
在應用程式碼可以存取使用中物件時，記憶體回收行程無法透過應用程式回收該物件。 應用程式即具有物件的強式參考。  
  
 弱式參考允許記憶體回收行程回收物件，同時仍然允許應用程式存取物件。 沒有強式參考時，除非回收物件，否則弱式參考僅在時間量不定期間才有效。 當您使用弱式參考時，應用程式仍然可以取得物件的強式參考，以防止回收該物件。 不過，記憶體回收行程在重新建立強式參考之前之前先取得物件，一定有其風險。  
  
 弱式參考適用於使用大量記憶體的物件，但可以在透過記憶體回收對其進行回收時輕鬆地予以重建。  
  
 假設您在 Windows Form 應用程式中的樹狀檢視顯示複雜階層式的選取選項給使用者。 如果基礎資料很大，則使用者參與應用程式中的其他作業時，將樹狀結構保留在記憶體不具效率。  
  
 當使用者切換離開至另一個應用程式的一部分時，您可以使用<xref:System.WeakReference>類別來建立樹狀結構的弱式參考，並終結所有的強式參考。 使用者切換回樹狀結構時，應用程式會嘗試取得樹狀結構的強式參考，如果成功，可以避免重新建構樹狀結構。  
  
 若要建立的物件的弱式參考，您建立<xref:System.WeakReference>使用要追蹤的物件執行個體。 接著將 <xref:System.WeakReference.Target%2A> 屬性設定為該物件，並將物件的原始參考設定為 `null`。 如需程式碼範例，請參閱<xref:System.WeakReference>類別庫中。  
  
## <a name="short-and-long-weak-references"></a>簡短和完整弱式參考  
 您可以建立簡短弱式參考或完整弱式參考︰  
  
-   Short  
  
     透過記憶體回收回收物件時，簡短弱式參考的目標會變成 `null`。 弱式參考本身是 Managed 物件，而且很容易進行記憶體回收，就像任何其他 Managed 物件一樣。  簡短的弱式參考是預設建構函式<xref:System.WeakReference>。  
  
-   Long  
  
     長弱式參考的物件後，要保留<xref:System.Object.Finalize%2A>呼叫方法。 這樣會重建物件，但是物件的狀態仍然無法預測。 若要使用的完整參考，請指定`true`中<xref:System.WeakReference>建構函式。  
  
     如果物件的型別沒有<xref:System.Object.Finalize%2A>方法，簡短的弱式參考功能適用於和弱式參考是有效僅限直到其收集的目標，這可能會發生安裝後的完成項執行。  
  
 若要建立強式參考，一次使用該物件轉型<xref:System.WeakReference.Target%2A>屬性<xref:System.WeakReference>物件的型別。 如果<xref:System.WeakReference.Target%2A>屬性會傳回`null`、 物件收集; 否則您可以繼續使用該物件，因為應用程式已重新取得它的強式參考。  
  
## <a name="guidelines-for-using-weak-references"></a>使用弱式參考的指導方針  
 只在物件狀態於完成之後無法預期時，才會在必要時使用完整弱式參考。  
  
 請避免使用小型物件的弱式參考，因為指標本身可能一樣大或較大。  
  
 請避免使用弱式參考作為記憶體管理問題的自動解決方案。 相反地，開發有效的快取原則來處理您的應用程式物件。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體回收](../../../docs/standard/garbage-collection/index.md)
