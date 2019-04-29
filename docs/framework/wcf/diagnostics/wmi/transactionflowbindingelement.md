---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641680"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="3516f-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="3516f-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="3516f-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="3516f-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3516f-104">語法</span><span class="sxs-lookup"><span data-stu-id="3516f-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3516f-105">方法</span><span class="sxs-lookup"><span data-stu-id="3516f-105">Methods</span></span>  
 <span data-ttu-id="3516f-106">TransactionFlowBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="3516f-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3516f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3516f-107">Properties</span></span>  
 <span data-ttu-id="3516f-108">TransactionFlowBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="3516f-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="3516f-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="3516f-109">IssuedTokens</span></span>  
 <span data-ttu-id="3516f-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="3516f-110">Data type: string</span></span>  
  
 <span data-ttu-id="3516f-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3516f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3516f-112">指定所發行安全性權杖標頭 (WS-Trust 的 IssuedTokens) 的需求。</span><span class="sxs-lookup"><span data-stu-id="3516f-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="3516f-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="3516f-113">TransactionProtocol</span></span>  
 <span data-ttu-id="3516f-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="3516f-114">Data type: string</span></span>  
  
 <span data-ttu-id="3516f-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3516f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3516f-116">服務用來使異動流動的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="3516f-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="3516f-117">異動</span><span class="sxs-lookup"><span data-stu-id="3516f-117">Transactions</span></span>  
 <span data-ttu-id="3516f-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="3516f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="3516f-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3516f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3516f-120">代表是否支援傳入異動。</span><span class="sxs-lookup"><span data-stu-id="3516f-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3516f-121">需求</span><span class="sxs-lookup"><span data-stu-id="3516f-121">Requirements</span></span>  
  
|<span data-ttu-id="3516f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="3516f-122">MOF</span></span>|<span data-ttu-id="3516f-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="3516f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3516f-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="3516f-124">Namespace</span></span>|<span data-ttu-id="3516f-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="3516f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3516f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3516f-126">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
