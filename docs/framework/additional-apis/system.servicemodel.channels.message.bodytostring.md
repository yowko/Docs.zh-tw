---
title: BodyToString 方法（System.servicemodel. 通道）
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215498"
---
# <a name="messagebodytostring-method"></a><span data-ttu-id="fd038-102">BodyToString 方法</span><span class="sxs-lookup"><span data-stu-id="fd038-102">Message.BodyToString Method</span></span>

<span data-ttu-id="fd038-103">藉由呼叫 <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> 方法，將訊息本文轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="fd038-103">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a><span data-ttu-id="fd038-104">參數</span><span class="sxs-lookup"><span data-stu-id="fd038-104">Parameters</span></span>

- <span data-ttu-id="fd038-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="fd038-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="fd038-106">用來將訊息主體轉換成字串的寫入器。</span><span class="sxs-lookup"><span data-stu-id="fd038-106">The writer that is used to convert the message body to a string.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd038-107">備註</span><span class="sxs-lookup"><span data-stu-id="fd038-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="fd038-108">`Message.BodyToString` 方法是內部的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="fd038-108">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="fd038-109">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="fd038-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd038-110">需求</span><span class="sxs-lookup"><span data-stu-id="fd038-110">Requirements</span></span>

<span data-ttu-id="fd038-111">**命名空間：** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="fd038-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="fd038-112">**元件：** System.servicemodel .dll</span><span class="sxs-lookup"><span data-stu-id="fd038-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="fd038-113">**.NET Framework 版本：** 自3.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="fd038-113">**.NET Framework versions:** Available since 3.0.</span></span>
