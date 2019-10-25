---
title: TlsStream. m_Worker 欄位（System.Net）
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.TlsStream.m_Worker
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: d335820d13e1e15e054e824a284615cdbf6c2094
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847189"
---
# <a name="tlsstreamm_worker-field"></a><span data-ttu-id="15a38-102">TlsStream. m_Worker 欄位</span><span class="sxs-lookup"><span data-stu-id="15a38-102">TlsStream.m_Worker Field</span></span>

<span data-ttu-id="15a38-103">表示 SSL 資料流程的狀態。</span><span class="sxs-lookup"><span data-stu-id="15a38-103">Represents the state of the SSL stream.</span></span>

## <a name="syntax"></a><span data-ttu-id="15a38-104">語法</span><span class="sxs-lookup"><span data-stu-id="15a38-104">Syntax</span></span>

```csharp
private SslState m_Worker;
```

## <a name="field-value"></a><span data-ttu-id="15a38-105">域值</span><span class="sxs-lookup"><span data-stu-id="15a38-105">Field value</span></span>

`System.Net.Security.SslState`  
<span data-ttu-id="15a38-106">SSL 資料流程的狀態。</span><span class="sxs-lookup"><span data-stu-id="15a38-106">The state of the SSL stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="15a38-107">備註</span><span class="sxs-lookup"><span data-stu-id="15a38-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="15a38-108">[`TlsStream.m_Worker`] 欄位是私用的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="15a38-108">The `TlsStream.m_Worker` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="15a38-109">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="15a38-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="15a38-110">需求</span><span class="sxs-lookup"><span data-stu-id="15a38-110">Requirements</span></span>

<span data-ttu-id="15a38-111">**命名空間︰** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="15a38-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="15a38-112">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="15a38-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="15a38-113">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="15a38-113">**.NET Framework versions:** Available since 2.0.</span></span>
