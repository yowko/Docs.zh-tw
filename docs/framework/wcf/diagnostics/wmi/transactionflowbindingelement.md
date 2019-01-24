---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: d0311837ebb8112d9492fb548492bcd3e10230e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514565"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="52b42-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="52b42-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="52b42-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="52b42-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b42-104">語法</span><span class="sxs-lookup"><span data-stu-id="52b42-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="52b42-105">方法</span><span class="sxs-lookup"><span data-stu-id="52b42-105">Methods</span></span>  
 <span data-ttu-id="52b42-106">TransactionFlowBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="52b42-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="52b42-107">屬性</span><span class="sxs-lookup"><span data-stu-id="52b42-107">Properties</span></span>  
 <span data-ttu-id="52b42-108">TransactionFlowBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="52b42-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="52b42-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="52b42-109">IssuedTokens</span></span>  
 <span data-ttu-id="52b42-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="52b42-110">Data type: string</span></span>  
  
 <span data-ttu-id="52b42-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="52b42-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52b42-112">指定所發行安全性權杖標頭 (WS-Trust 的 IssuedTokens) 的需求。</span><span class="sxs-lookup"><span data-stu-id="52b42-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="52b42-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="52b42-113">TransactionProtocol</span></span>  
 <span data-ttu-id="52b42-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="52b42-114">Data type: string</span></span>  
  
 <span data-ttu-id="52b42-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="52b42-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52b42-116">服務用來使異動流動的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="52b42-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="52b42-117">異動</span><span class="sxs-lookup"><span data-stu-id="52b42-117">Transactions</span></span>  
 <span data-ttu-id="52b42-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="52b42-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="52b42-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="52b42-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52b42-120">代表是否支援傳入異動。</span><span class="sxs-lookup"><span data-stu-id="52b42-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52b42-121">需求</span><span class="sxs-lookup"><span data-stu-id="52b42-121">Requirements</span></span>  
  
|<span data-ttu-id="52b42-122">MOF</span><span class="sxs-lookup"><span data-stu-id="52b42-122">MOF</span></span>|<span data-ttu-id="52b42-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="52b42-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="52b42-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="52b42-124">Namespace</span></span>|<span data-ttu-id="52b42-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="52b42-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52b42-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52b42-126">See also</span></span>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
