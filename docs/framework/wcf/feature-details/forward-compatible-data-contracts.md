---
title: 向前相容資料合約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 95a72d5d09538bc6f663f2376c7f8f928909cd57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492202"
---
# <a name="forward-compatible-data-contracts"></a><span data-ttu-id="08d8c-102">向前相容資料合約</span><span class="sxs-lookup"><span data-stu-id="08d8c-102">Forward-Compatible Data Contracts</span></span>
<span data-ttu-id="08d8c-103">一項功能的 Windows Communication Foundation (WCF) 是資料合約系統的合約可以隨著時間持續發展，特點。</span><span class="sxs-lookup"><span data-stu-id="08d8c-103">A feature of the Windows Communication Foundation (WCF) data contract system is that contracts can evolve over time in nonbreaking ways.</span></span> <span data-ttu-id="08d8c-104">也就是說，有舊版資料合約的用戶端可以與有新版相同資料合約的服務通訊，或是有新版資料合約的用戶端可以與有舊版相同資料合約通訊。</span><span class="sxs-lookup"><span data-stu-id="08d8c-104">That is, a client with an older version of a data contract can communicate with a service with a newer version of the same data contract, or a client with a newer version of a data contract can communicate with an older version of the same data contract.</span></span> <span data-ttu-id="08d8c-105">如需詳細資訊，請參閱[最佳做法： 資料合約版本控制](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="08d8c-105">For more information, see [Best Practices: Data Contract Versioning](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).</span></span>  
  
 <span data-ttu-id="08d8c-106">建立新版的現有資料合約時，您可以根據需要套用大部分的版本控制功能。</span><span class="sxs-lookup"><span data-stu-id="08d8c-106">You can apply most of the versioning features on an as-needed basis when new versions of an existing data contract are created.</span></span> <span data-ttu-id="08d8c-107">不過，一個版本控制功能，*往返*，必須內建的第一個版本中的型別才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="08d8c-107">However, one versioning feature, *round-tripping*, must be built into the type from the first version in order to work properly.</span></span>  
  
## <a name="round-tripping"></a><span data-ttu-id="08d8c-108">往返</span><span class="sxs-lookup"><span data-stu-id="08d8c-108">Round-Tripping</span></span>  
 <span data-ttu-id="08d8c-109">當資料從新版本傳遞到舊版本，然後回到新版本的資料合約時，即代表發生往返。</span><span class="sxs-lookup"><span data-stu-id="08d8c-109">Round-tripping occurs when data passes from a new version to an old version and back to the new version of a data contract.</span></span> <span data-ttu-id="08d8c-110">使用往返時，任何資料保證都不會遺失。</span><span class="sxs-lookup"><span data-stu-id="08d8c-110">Round-tripping guarantees that no data is lost.</span></span> <span data-ttu-id="08d8c-111">如果啟用往返，就會使類型向前相容於資料合約版本控制模型所支援的任何未來變更。</span><span class="sxs-lookup"><span data-stu-id="08d8c-111">Enabling round-tripping makes the type forward-compatible with any future changes supported by the data contract versioning model.</span></span>  
  
 <span data-ttu-id="08d8c-112">若要啟用特定類型的往返，類型必須實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面，</span><span class="sxs-lookup"><span data-stu-id="08d8c-112">To enable round-tripping for a particular type, the type must implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span> <span data-ttu-id="08d8c-113">這個介面則包含屬性 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (傳回 <xref:System.Runtime.Serialization.ExtensionDataObject> 型別)。</span><span class="sxs-lookup"><span data-stu-id="08d8c-113">The interface contains one property, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (returning the <xref:System.Runtime.Serialization.ExtensionDataObject> type).</span></span> <span data-ttu-id="08d8c-114">該屬性會儲存來自目前版本未知的資料合約未來版本的任何資料。</span><span class="sxs-lookup"><span data-stu-id="08d8c-114">The property stores any data from future versions of the data contract that is unknown to the current version.</span></span>  
  
### <a name="example"></a><span data-ttu-id="08d8c-115">範例</span><span class="sxs-lookup"><span data-stu-id="08d8c-115">Example</span></span>  
 <span data-ttu-id="08d8c-116">下列資料合約未向前相容於未來變更。</span><span class="sxs-lookup"><span data-stu-id="08d8c-116">The following data contract is not forward-compatible with future changes.</span></span>  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 <span data-ttu-id="08d8c-117">若要使類型向前相容於未來變更 (例如新增名為 "phoneNumber" 的新資料成員)，請實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面。</span><span class="sxs-lookup"><span data-stu-id="08d8c-117">To make the type compatible with future changes (such as adding a new data member named "phoneNumber"), implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 <span data-ttu-id="08d8c-118">當 WCF 基礎結構遇到不是原始的資料合約的一部分的資料時，資料是儲存在屬性，並保留。</span><span class="sxs-lookup"><span data-stu-id="08d8c-118">When the WCF infrastructure encounters data that is not part of the original data contract, the data is stored in the property and preserved.</span></span> <span data-ttu-id="08d8c-119">這個資料只會以暫時儲存的方式處理。</span><span class="sxs-lookup"><span data-stu-id="08d8c-119">It is not processed in any other way except for temporary storage.</span></span> <span data-ttu-id="08d8c-120">如果物件傳回到其產生位置，原始 (未知的) 資料也會傳回。</span><span class="sxs-lookup"><span data-stu-id="08d8c-120">If the object is returned back to where it originated, the original (unknown) data is also returned.</span></span> <span data-ttu-id="08d8c-121">因此，這代表資料往返於原始端點之間，而且沒有遺失。</span><span class="sxs-lookup"><span data-stu-id="08d8c-121">Therefore, the data has made a round trip to and from the originating endpoint without loss.</span></span> <span data-ttu-id="08d8c-122">不過請注意，如果產生物件的端點要求處理資料，上述情況便不成立，端點也就必須偵測與配合變更。</span><span class="sxs-lookup"><span data-stu-id="08d8c-122">Note, however, that if the originating endpoint required the data to be processed, that expectation is unmet, and the endpoint must somehow detect and accommodate the change.</span></span>  
  
 <span data-ttu-id="08d8c-123"><xref:System.Runtime.Serialization.ExtensionDataObject> 型別不包含公用方法或屬性，</span><span class="sxs-lookup"><span data-stu-id="08d8c-123">The <xref:System.Runtime.Serialization.ExtensionDataObject> type contains no public methods or properties.</span></span> <span data-ttu-id="08d8c-124">因此無法直接存取儲存在 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> 屬性中的資料。</span><span class="sxs-lookup"><span data-stu-id="08d8c-124">Thus, it is impossible to get direct access to the data stored inside the <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property.</span></span>  
  
 <span data-ttu-id="08d8c-125">在 `ignoreExtensionDataObject` 建構函式中將 `true` 設定為 <xref:System.Runtime.Serialization.DataContractSerializer> 或針對 <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> 將 `true` 屬性設定為 <xref:System.ServiceModel.ServiceBehaviorAttribute>，即可關閉往返功能。</span><span class="sxs-lookup"><span data-stu-id="08d8c-125">The round-tripping feature may be turned off, either by setting `ignoreExtensionDataObject` to `true` in the <xref:System.Runtime.Serialization.DataContractSerializer> constructor or by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> property to `true` on the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="08d8c-126">此功能關閉時，還原序列化程式將不會填入 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> 屬性，而且序列化程式將不會發出屬性內容。</span><span class="sxs-lookup"><span data-stu-id="08d8c-126">When this feature is off, the deserializer will not populate the <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property, and the serializer will not emit the contents of the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d8c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08d8c-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 [<span data-ttu-id="08d8c-128">資料合約版本控制</span><span class="sxs-lookup"><span data-stu-id="08d8c-128">Data Contract Versioning</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [<span data-ttu-id="08d8c-129">最佳做法：資料合約版本設定</span><span class="sxs-lookup"><span data-stu-id="08d8c-129">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
