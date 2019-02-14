---
title: HOW TO：控制服務執行個體
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 06324b30d2fbd68a12619375024b9f86019adbb1
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260957"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="e95ea-102">HOW TO：控制服務執行個體</span><span class="sxs-lookup"><span data-stu-id="e95ea-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="e95ea-103">設定服務的執行個體模式，可讓您指定 <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (及其相關之使用者定義的服務物件) 建立的時機。</span><span class="sxs-lookup"><span data-stu-id="e95ea-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="e95ea-104">如需可能的模式，請參閱 <xref:System.ServiceModel.InstanceContextMode> 列舉。</span><span class="sxs-lookup"><span data-stu-id="e95ea-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="e95ea-105">如需行為的詳細資訊，請參閱[設定和擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="e95ea-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="e95ea-106">如需實用範例，請參閱[行為](../../../../docs/framework/wcf/samples/behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="e95ea-106">For working examples, see [Behaviors](../../../../docs/framework/wcf/samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="e95ea-107">使用程式碼控制服務執行個體存留期</span><span class="sxs-lookup"><span data-stu-id="e95ea-107">To control the service instance lifetime using code</span></span>  
  
1.  <span data-ttu-id="e95ea-108">將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 套用至服務類別。</span><span class="sxs-lookup"><span data-stu-id="e95ea-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2.  <span data-ttu-id="e95ea-109">將 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性設定為下列其中一值：<xref:System.ServiceModel.InstanceContextMode.PerCall>、<xref:System.ServiceModel.InstanceContextMode.PerSession> 或 <xref:System.ServiceModel.InstanceContextMode.Single>。</span><span class="sxs-lookup"><span data-stu-id="e95ea-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="e95ea-110">範例</span><span class="sxs-lookup"><span data-stu-id="e95ea-110">Example</span></span>  
 <span data-ttu-id="e95ea-111">下列程式碼範例會將 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性 (Property) 設定為 <xref:System.ServiceModel.InstanceContextMode.PerCall>。</span><span class="sxs-lookup"><span data-stu-id="e95ea-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e95ea-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e95ea-112">See also</span></span>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="e95ea-113">服務：行為範例</span><span class="sxs-lookup"><span data-stu-id="e95ea-113">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
