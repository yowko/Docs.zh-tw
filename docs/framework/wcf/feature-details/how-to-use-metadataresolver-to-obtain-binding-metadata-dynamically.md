---
title: "HOW TO：使用 MetadataResolver 來動態取得繫結中繼資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab95212d0f7b57b2bc076bed862b3d07c3c93df9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="3de44-102">HOW TO：使用 MetadataResolver 來動態取得繫結中繼資料</span><span class="sxs-lookup"><span data-stu-id="3de44-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="3de44-103">本主題示範如何使用 <xref:System.ServiceModel.Description.MetadataResolver> 類別來動態取得繫結中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3de44-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="3de44-104">若要動態取得繫結中繼資料</span><span class="sxs-lookup"><span data-stu-id="3de44-104">To dynamically obtain binding metadata</span></span>  
  
1.  <span data-ttu-id="3de44-105">建立具有中繼資料端點位址的 <xref:System.ServiceModel.EndpointAddress> 物件。</span><span class="sxs-lookup"><span data-stu-id="3de44-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  <span data-ttu-id="3de44-106">呼叫 <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>，它會傳入服務類型和中繼資料端點位址。</span><span class="sxs-lookup"><span data-stu-id="3de44-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="3de44-107">這麼做會傳回實作指定之合約的端點集合。</span><span class="sxs-lookup"><span data-stu-id="3de44-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="3de44-108">只有繫結資訊會從中繼資料匯出，不會匯出合約資訊。</span><span class="sxs-lookup"><span data-stu-id="3de44-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="3de44-109">並改用所提供的合約。</span><span class="sxs-lookup"><span data-stu-id="3de44-109">The supplied contract is used instead.</span></span>  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  <span data-ttu-id="3de44-110">您接著便可以逐一查看服務端點的集合，以擷取所需的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="3de44-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="3de44-111">下列程式碼會逐一查看端點、建立服務用戶端物件 (此物件會傳入與目前端點關聯的繫結和位址)，然後再呼叫服務上的方法。</span><span class="sxs-lookup"><span data-stu-id="3de44-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
    ```  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3de44-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3de44-112">See Also</span></span>  
 [<span data-ttu-id="3de44-113">中繼資料</span><span class="sxs-lookup"><span data-stu-id="3de44-113">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
