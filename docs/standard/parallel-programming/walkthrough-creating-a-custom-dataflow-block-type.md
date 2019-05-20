---
title: 逐步解說：建立自訂資料流程區塊類型
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62e2a25e48ead730112a37af451d64c6ccc2e141
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593444"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>逐步解說：建立自訂資料流程區塊類型
雖然 TPL 資料流程式庫提供數個啟用各種不同功能的資料流程區塊類型，但您也可以建立自訂的區塊類型。 本文件說明如何建立會實作自訂行為的資料流程區塊類型之兩種方式。  
  
## <a name="prerequisites"></a>必要條件  
 在您閱讀本文件之前，請閱讀[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)。  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>定義滑動視窗資料流程區塊  
 請考慮要求緩衝處理輸入值，然後以滑動視窗的方式輸出的資料流程應用程式。 例如，針對輸入值 {0, 1, 2, 3, 4, 5} 且視窗大小為三個，滑動視窗資料流程區塊會產生輸出陣列 {0, 1, 2}、{1, 2, 3}、{2, 3, 4} 和 {3, 4, 5}。 下列各節將說明建立會實作自訂行為的資料流程區塊類型之兩種方式。 第一種技術會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> 方法，將 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 物件和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 物件的功能結合為單一傳播程式區塊。 第二種技術會定義一個衍生自 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> 的類別，並結合現有的功能以執行自訂行為。  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>使用封裝方法來定義滑動視窗資料流程區塊  
 下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>方法，從目標與來源建立一個傳播程式區塊。 傳播程式區塊可讓來源區塊和目標區塊作為資料的接收者與傳送者。  
  
 當您需要自訂的資料流程功能，但您不需要提供額外方法、屬性或欄位的類型時，這個技術非常有用。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>衍生自 IPropagatorBlock 以定義滑動視窗資料流程區塊  
 下列範例顯示 `SlidingWindowBlock` 類別。 此類別衍生自 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>，如此一來它就可以同時作為資料來源與目標。 如同先前的範例，`SlidingWindowBlock` 類別建置於現有的資料流程區塊類型上。 不過，`SlidingWindowBlock` 類別也會實作 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> 介面所需的方法。 這些方法全都會將工作轉寄給預先定義的資料流程區塊類型成員。 例如，`Post` 方法會將工作延後到 `m_target` 資料成員，這也是一個 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 物件。  
  
 當您需要自訂的資料流程功能，也需要提供額外方法、屬性或欄位的類型時，這個技術非常有用。 例如，`SlidingWindowBlock` 類別也衍生自 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601>，如此一來它就可以提供 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 和 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> 方法。 `SlidingWindowBlock` 類別也會透過提供 `WindowSize` 屬性來示範擴充性，該屬性會擷取滑動視窗中的項目數目。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>完整範例  
 下列範例將示範本逐步解說的完整程式碼。 它也會示範如何使用寫入區塊、從區塊讀取，並將結果列印至主控台之方法中的兩個滑動視窗區塊。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a>另請參閱

- [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
