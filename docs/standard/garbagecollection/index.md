---
title: "記憶體回收"
description: "記憶體回收"
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: db39a0f5-e363-490f-a7e6-adb9a6ff2a8c
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: 2406a03fa64eb02c70f05c1e8240e4bc5981e98d

---

# <a name="garbage-collection"></a>記憶體回收

記憶體回收是 .NET Managed 程式碼平台的其中一個最重要功能。 記憶體回收行程 (GC) 管理如何配置和釋放記憶體。 您不需要知道如何配置和釋放記憶體，或管理使用該記憶體之物件的存留期。 只要方塊化「新建」物件或實值類型，就會進行配置。 配置的速度通常很快。 沒有足夠的記憶體可配置物件時，GC 必須收集並處置廢棄記憶體，讓記憶體可用於新的配置。 這個程序稱為「記憶體回收」。

記憶體回收行程會當做自動記憶體管理員。 它提供了下列優點：

*   可讓您開發應用程式，而不需要釋放記憶體。
*   有效率地在 Managed 堆積上配置物件。
*   回收不再使用的物件、清除其記憶體，並且讓記憶體可供未來的配置使用。 Managed 物件在開始時會自動取得乾淨的內容，因此其建構函式不需要初始化每個資料欄位。
*   確保某個物件無法使用另一個物件的內容，藉以提供記憶體安全性。

.NET GC 是層代式，並且具有 3 個層代。 每個層代都有用於儲存已配置物件的專屬堆積。 大部分物件是短暫存留或長期存留，都有其基本原則。 層代 0 是一開始配置物件的位置。 物件通常不會存留過第一個層代，因為它們在進行下一次記憶體回收之前都無法再使用 (超出範圍)。 因為層代 0 的相關聯堆積很小，所以很快就能回收層代 0。 層代 1 實際上是第二個機會空間。 短暫存留但升級層代 0 回收的物件 (通常根據最佳計時) 會移至層代 1。層代 1 的相關聯堆積也很小，因此回收也十分快速。 前兩個堆積都會很小，原因是物件會回收或升級到下一個層代堆積。 層代 2 是所有長期存留物件所在的位置。 層代 2 堆積可以成長地非常大，因為它所含的物件可以存活很長的時間，而且沒有層代 3 堆積可以進一步升級物件。

GC 已有稱為大型物件堆積 (LOH) 之大型物件的堆積。 它是保留供具有 85,000 (含) 以上位元組的物件使用。 具有 85k 元素的位元組陣列 (Byte[]) 是大型物件的範例。 大型物件不會配置給層代式堆積，但會直接配置給 LOH。

層代 2 和 LOH 回收對於長時間執行的程式可能需要大量時間，或操作大量資料。 大型伺服器程式已知有 10 幾個 GB 的堆積。 GC 會運用各種技術，降低它封鎖程式執行的時間量。 主要方式是盡可能在背景執行緒上執行大部分記憶體回收工作，而不干擾程式執行。 GC 也會公開數種方式，讓開發人員影響其行為，而這相當適合改善效能。

## <a name="related-topics"></a>相關主題

標題 | 說明
----- | ----------- 
[自動記憶體管理和記憶體回收](gc.md) | 介紹 .NET 中記憶體管理的基本概念
[記憶體回收的基本概念](fundamentals.md) | 描述記憶體回收運作方式、如何在 Managed 堆積上配置物件，以及其他核心概念。
[引發的集合](induced.md) | 描述如何進行記憶體回收。
[延遲模式](latency.md) | 描述判斷記憶體回收干擾程度的模式。
[弱式參考](weak-references.md) | 描述下列功能：允許記憶體回收行程回收物件，同時仍然允許應用程式存取該物件。
 
## <a name="reference"></a>參考資料

[System.GC](xref:System.GC)

[System.GCCollectionMode](xref:System.GCCollectionMode)

[System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode)

[System.Runtime.GCSettings](xref:System.Runtime.GCSettings)

[GCSettings.LargeObjectHeapCompactionMode](xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode)

[Object.Finalize](xref:System.Object.Finalize)

[System.IDisposable](xref:System.IDisposable)

## <a name="see-also"></a>另請參閱

[清除 Unmanaged 資源](unmanaged.md)




<!--HONumber=Nov16_HO1-->


