---
title: 在 Windows 8、Windows 8.1 或 Windows 10 上執行 .NET Framework 1.1 應用程式
description: 描述如何適應需要 .NET 框架 1.1 的應用，Windows 作業系統的許多版本不再支援 .NET 框架 1.1。
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 6d1cb2f9251bba96d0a378bf4dbab9f7da267037
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111786"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>在 Windows 8、Windows 8.1 或 Windows 10 上執行 .NET Framework 1.1 應用程式

在 Windows 8、Windows 8.1、Windows 伺服器 2012、Windows 伺服器 2012 R2 或 Windows 10 作業系統上不支援 .NET 框架 1.1。 在某些情況下，需要 .NET 框架 1.1 才能運行應用。 在這些情況下，請與您的獨立軟體廠商 （ISV） 聯繫，將應用升級到在 .NET 框架 3.5 SP1 或更高版本中運行。 有關詳細資訊，請參閱從[.NET 框架 1.1 進行遷移](../migration-guide/migrating-from-the-net-framework-1-1.md)。

## <a name="install-net-framework-11-from-a-cd-or-download-center"></a>從 CD 或下載中心安裝 .NET 框架 1.1

無法在 Windows 8、Windows 8.1、Windows 伺服器 2012、Windows 伺服器 2012 R2 或從 CD 或下載中心手動安裝 Windows 10。 它不再受支援。 如果您嘗試安裝該套件，便會顯示下面錯誤訊息：「安裝程式無法繼續，因為這個 .NET Framework 版本與之前安裝的版本不相容」。 要解決此問題，請安裝[.NET 框架 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22)。 此版本包括 .NET 框架 2.0（以下版本 .NET 框架 1.1），Windows 8、Windows 8.1 和 Windows 10 支援。 您應該始終嘗試先安裝應用，以確定它是否將自動更新為更高版本的 .NET Framework。 如果沒有，請與 ISV 聯繫以進行應用更新。

## <a name="see-also"></a>另請參閱

- [從 .NET Framework 1.1 移轉](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5](dotnet-35-windows-10.md)
