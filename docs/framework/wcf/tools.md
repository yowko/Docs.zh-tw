---
title: Windows Communication Foundation 工具
description: 瞭解專為讓您更輕鬆地建立、部署和管理 WCF 應用程式而設計的 WCF 工具。 從命令提示字元執行這些工具。
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, tools
- Windows Communication Foundation, tools
ms.assetid: 399a47b4-bfea-434b-8e83-f76b5063d79d
ms.openlocfilehash: acc142e8e3108a827b63cf013b818d30b5dcaa52
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245962"
---
# <a name="windows-communication-foundation-tools"></a>Windows Communication Foundation 工具
Microsoft Windows Communication Foundation （WCF）工具的設計，是為了讓您更輕鬆地建立、部署和管理 WCF 應用程式。 本章節內容包含工具的詳細資訊。 請注意，並不支援這些工具。  
  
 您可以從命令列執行所有工具。  
  
 下表列出這些工具，並提供簡短描述。  
  
|工具|描述|  
|----------|-----------------|  
|[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)|從中繼資料文件產生服務模型程式碼，以及從服務模型程式碼產生中繼資料文件。|  
|[尋找私密金鑰工具 (FindPrivateKey.exe)](find-private-key-tool-findprivatekey-exe.md)|從指定的存放區擷取私密金鑰。|  
|[ServiceModel 註冊工具 (ServiceModelReg.exe)](servicemodelreg-exe.md)|管理單一電腦上 ServiceModel 的註冊和移除註冊。|  
|[COM+ 服務模型設定工具 (ComSvcConfig.exe)](com-service-model-configuration-tool-comsvcconfig-exe.md)|設定要公開為 Web 服務的 COM+ 介面。|  
|[設定編輯器工具 (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)|建立和修改 WCF 服務的組態設定。|  
|[服務追蹤檢視器工具 (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md)|協助您檢視、分組與篩選追蹤訊息，以便診斷、修復和驗證 WCF 服務的各種問題。|  
|[WS-AtomicTransaction 設定公用程式 (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)|使用命令列工具來設定基本 WS-AtomicTransaction 支援設定。|  
|[WS-AtomicTransaction 組態 MMC 嵌入式管理單元](ws-atomictransaction-configuration-mmc-snap-in.md)|使用 MMC 嵌入式管理單元來設定基本 WS-AtomicTransaction 支援設定。|  
|[WorkFlow 服務登錄工具 (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md)|註冊 Windows 工作流程服務。|  
|[WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)|裝載程式庫（* .dll）檔案中包含的 WCF 服務|  
|[WCF 測試用戶端 (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)|一種 GUI 工具，可讓您輸入任意型別的參數、將該輸入送出至服務，以及檢視服務傳回的回應。|  
|[Contract-First 工具](contract-first-tool.md)|從 XSD 資料合約建立程式碼類別的 Visual Studio 建置工作。|  
  
 ServiceModelReg.exe、WsatConfig.exe 和 ComSvcConfig.exe 除外，上述的工具全都隨附於 Windows SDK，位於 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin 資料夾下。  這三個特定工具位於 C:\Windows\Microsoft.NET\Framework\v3.0\Windows Communication Foundation 下。
