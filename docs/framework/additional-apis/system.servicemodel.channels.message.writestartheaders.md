---
title: WriteStartHeaders 方法（System.servicemodel. 通道）
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: a2c82ee4029c7af0396219f5ded8c999fd01d65b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451175"
---
# <a name="messagewritestartheaders-method"></a><span data-ttu-id="6a207-102">WriteStartHeaders 方法</span><span class="sxs-lookup"><span data-stu-id="6a207-102">Message.WriteStartHeaders Method</span></span>

<span data-ttu-id="6a207-103">藉由呼叫 <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> 方法，將開始標頭寫入至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="6a207-103">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a><span data-ttu-id="6a207-104">參數</span><span class="sxs-lookup"><span data-stu-id="6a207-104">Parameters</span></span>

- <span data-ttu-id="6a207-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="6a207-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="6a207-106">用來將開始標頭寫入 XML 檔案的寫入器。</span><span class="sxs-lookup"><span data-stu-id="6a207-106">The writer that is used to write the start header into an XML file.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a207-107">備註</span><span class="sxs-lookup"><span data-stu-id="6a207-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6a207-108">`Message.WriteStartHeaders` 方法是內部的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="6a207-108">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6a207-109">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="6a207-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a207-110">需求</span><span class="sxs-lookup"><span data-stu-id="6a207-110">Requirements</span></span>

<span data-ttu-id="6a207-111">**命名空間︰** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="6a207-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="6a207-112">**元件：** System.servicemodel .dll</span><span class="sxs-lookup"><span data-stu-id="6a207-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="6a207-113">**.NET Framework 版本：** 自3.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="6a207-113">**.NET Framework versions:** Available since 3.0.</span></span>
