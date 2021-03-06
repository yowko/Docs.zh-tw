---
title: 使用 Azure SDK for .NET 時設定 proxy 伺服器
description: 使用 HTTP [S] _PROXY 環境變數來定義適用于 .NET 的 Azure SDK 的 PROXY
ms.date: 12/10/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.openlocfilehash: 64d525f8a6c277a5ac383dfded828f2fd3cfd744
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701071"
---
# <a name="configure-a-proxy-server-when-using-the-azure-sdk-for-net"></a>使用 Azure SDK for .NET 時設定 proxy 伺服器

如果您的組織需要使用 proxy 伺服器來存取網際網路資源，您將需要使用 proxy 伺服器資訊來設定環境變數，以使用 Azure SDK for .NET。  

## <a name="configuration-using-environment-variables"></a>使用環境變數進行設定

根據您的 proxy 伺服器使用的是 HTTP 或 HTTPS，您將會分別設定環境 `HTTP_PROXY` 變數 `HTTPS_PROXY` 。 Proxy 伺服器 URL 的格式 `http[s]://[username:password@]<ip_address_or_hostname>:<port>/` `username:password` 為選擇性的組合。 若要取得 proxy 伺服器的 IP 位址或主機名稱、埠和認證，請洽詢您的網路系統管理員。

下列範例示範如何在命令 shell 中設定適當的環境變數 (Windows) 和 bash (Linux/Mac) 環境。  設定適當的環境變數之後，將會導致 Azure SDK for .NET 在執行時間使用 proxy 伺服器。

### <a name="cmd"></a>[cmd](#tab/cmd)

```cmd
rem Non-authenticated HTTP server:
set HTTP_PROXY=http://10.10.1.10:1180

rem Authenticated HTTP server:
set HTTP_PROXY=http://username:password@10.10.1.10:1180

rem Non-authenticated HTTPS server:
set HTTPS_PROXY=http://10.10.1.10:1180

rem Authenticated HTTPS server:
set HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

### <a name="bash"></a>[bash](#tab/bash)

```bash
# Non-authenticated HTTP server:
HTTP_PROXY=http://10.10.1.10:1180

# Authenticated HTTP server:
HTTP_PROXY=http://username:password@10.10.1.10:1180

# Non-authenticated HTTPS server:
HTTPS_PROXY=http://10.10.1.10:1180

# Authenticated HTTPS server:
HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

---
