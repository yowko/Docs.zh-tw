---
title: UnsafeNclNativeMethods 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 46756a0d1d69b4768dbb8dcdd7ab098d3f1849bf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990307"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="86d5d-102">UnsafeNclNativeMethods 類別</span><span class="sxs-lookup"><span data-stu-id="86d5d-102">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="86d5d-103">包含可匯入不安全的原生網路方法的類別。</span><span class="sxs-lookup"><span data-stu-id="86d5d-103">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="86d5d-104">這個類別無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="86d5d-104">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="86d5d-105">這個類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="86d5d-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="86d5d-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="86d5d-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="86d5d-107">NativePKI 類別</span><span class="sxs-lookup"><span data-stu-id="86d5d-107">NativePKI class</span></span>

<span data-ttu-id="86d5d-108">包含從 crypt32.dll 匯入的方法。</span><span class="sxs-lookup"><span data-stu-id="86d5d-108">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="86d5d-109">這些方法會在使用超文字安全傳輸通訊協定（HTTPS）時處理憑證。</span><span class="sxs-lookup"><span data-stu-id="86d5d-109">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="86d5d-110">這個類別無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="86d5d-110">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="86d5d-111">NativePKI. FindClientCertificates 方法</span><span class="sxs-lookup"><span data-stu-id="86d5d-111">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="86d5d-112">探索要傳送至伺服器的可用用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="86d5d-112">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="86d5d-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="86d5d-113">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="86d5d-114">可用用戶端憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="86d5d-114">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="86d5d-115">需求</span><span class="sxs-lookup"><span data-stu-id="86d5d-115">Requirements</span></span>

<span data-ttu-id="86d5d-116">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="86d5d-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="86d5d-117">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="86d5d-117">**Assembly:** System (in System.dll)</span></span>
