---
title: 在 Windows 8、Windows 8.1 或 Windows 10 上執行 .NET Framework 1.1 應用程式
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1364eebf4d94a117a3ee7f0912b6ff4090e93853
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960040"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>在 Windows 8、Windows 8.1 或 Windows 10 上執行 .NET Framework 1.1 應用程式

Windows 8、Windows 8.1、Windows Server 2012、[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]或 Windows 10 作業系統不支援 .NET Framework 1.1。 在某些情況下，會將 .NET Framework 1.1 明確視為執行應用程式所需的必要項。 在這些情況下，您應該連絡您的獨立軟體廠商 (ISV) 將應用程式升級，以便在 .NET Framework 3.5 SP1 或更新版本上執行。 如需其他資訊，請參閱[從 .NET Framework 1.1 移轉](../migration-guide/migrating-from-the-net-framework-1-1.md)。

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>從光碟或下載中心安裝 .NET Framework 1.1

您無法在 Windows 8、Windows 8.1、Windows Server 2012、[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]或 Windows 10 上手動安裝 .NET Framework 1.1。 它不再受支援。 如果您嘗試安裝該套件，便會顯示下面錯誤訊息：「安裝程式無法繼續，因為這個 .NET Framework 版本與之前安裝的版本不相容」。 若要解決這個問題，請安裝 [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22)。 此版本包含 Windows 8、Windows 8.1 和 Windows 10 上支援的 .NET Framework 2.0 （.NET Framework 1.1 之後的版本）。 您一定要先嘗試安裝應用程式，判斷它是否會自動更新為較新版本的 .NET Framework。 如果沒有，請連絡您的 ISV 以取得應用程式更新。

## <a name="see-also"></a>請參閱

- [從 .NET Framework 1.1 移轉](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5](dotnet-35-windows-10.md)
