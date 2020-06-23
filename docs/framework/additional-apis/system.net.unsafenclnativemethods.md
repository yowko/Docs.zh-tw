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
# <a name="unsafenclnativemethods-class"></a>UnsafeNclNativeMethods 類別

包含可匯入不安全的原生網路方法的類別。 這個類別無法被繼承。

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> 這個類別是內部的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="nativepki-class"></a>NativePKI 類別

包含從 crypt32.dll 匯入的方法。 這些方法會在使用超文字安全傳輸通訊協定（HTTPS）時處理憑證。 這個類別無法被繼承。

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a>NativePKI. FindClientCertificates 方法

探索要傳送至伺服器的可用用戶端憑證。

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a>傳回值

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

可用用戶端憑證的集合。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）
