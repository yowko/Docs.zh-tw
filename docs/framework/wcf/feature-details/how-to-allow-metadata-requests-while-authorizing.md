---
title: HOW TO：授權時同時允許中繼資料要求
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 2f855080cf3ba4cee08470af77c52945e47a2ec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489631"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="01d03-102">HOW TO：授權時同時允許中繼資料要求</span><span class="sxs-lookup"><span data-stu-id="01d03-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="01d03-103">自訂授權期間，可能需要允許處理中繼資料的要求。</span><span class="sxs-lookup"><span data-stu-id="01d03-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="01d03-104">下列主題逐步解說要驗證如此要求的步驟。</span><span class="sxs-lookup"><span data-stu-id="01d03-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="01d03-105">如需 Windows Communication Foundation (WCF) 授權的詳細資訊，請參閱[授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="01d03-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="01d03-106">授權時同時允許中繼資料要求</span><span class="sxs-lookup"><span data-stu-id="01d03-106">To allow metadata requests during authorization</span></span>  
  
1.  <span data-ttu-id="01d03-107">建立 <xref:System.ServiceModel.ServiceAuthorizationManager> 類別的延伸。</span><span class="sxs-lookup"><span data-stu-id="01d03-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2.  <span data-ttu-id="01d03-108">覆寫 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="01d03-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="01d03-109">方法會依據是否允許授權而傳回 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="01d03-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="01d03-110">關於目前程式的資訊可在 <xref:System.ServiceModel.OperationContext> 傳給方法的參數找到。</span><span class="sxs-lookup"><span data-stu-id="01d03-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3.  <span data-ttu-id="01d03-111">在覆寫中，如以下範例所示，檢查合約名稱、命名空間以及動作。</span><span class="sxs-lookup"><span data-stu-id="01d03-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="01d03-112">若條件有效，會傳回 `true.`</span><span class="sxs-lookup"><span data-stu-id="01d03-112">If the conditions are valid, then return `true.`</span></span>  
  
4.  <span data-ttu-id="01d03-113">使用擴充點套用類別。</span><span class="sxs-lookup"><span data-stu-id="01d03-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="01d03-114">如需詳細資訊，請參閱[How to： 建立自訂授權管理員服務](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)。</span><span class="sxs-lookup"><span data-stu-id="01d03-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d03-115">範例</span><span class="sxs-lookup"><span data-stu-id="01d03-115">Example</span></span>  
 <span data-ttu-id="01d03-116">下例範例示範 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="01d03-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="01d03-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01d03-117">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="01d03-118">授權</span><span class="sxs-lookup"><span data-stu-id="01d03-118">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="01d03-119">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="01d03-119">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
