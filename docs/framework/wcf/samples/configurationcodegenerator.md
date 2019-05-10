---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: a01300024f89a0a189045d80622121f7db739a39
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912416"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator 是可供您用來公開自訂通道實作給組態系統的工具。 這將允許您的自訂通道使用者使用 .config 檔案設定通道，就像平常使用 `NetTcpBinding` 來設定系統提供的繫結 (例如 `TcpTransportBindingElement`) 或自訂繫結一般。  
  
 使用新的 `BindingElement` 或 `Binding` 撰寫自訂通道並將它公開給程式設計模型時，您必須建立一組類別，讓 `BindingElement` 或 `Binding` 可透過使用 .config 檔案來加以設定。 您可以使用 ConfigurationCodeGenerator 工具產生這些類別，並增進客戶的使用體驗。  
  
### <a name="to-build-the-tool"></a>建置工具  
  
1. 若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
2. 建置方案時，會產生一個檔案：ConfigurationCodeGenerator.exe. 檔案 SampleRun.cmd 有一個示範如何使用此工具產生的類別的範例命令列[傳輸：UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例。  
  
### <a name="to-run-the-tool"></a>執行工具  
  
1. 如果您同時有自訂 `BindingElement` 型別和自訂 `Binding` 型別，請在命令提示字元中輸入下列命令：  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     如果您只有自訂 `BindingElement` 型別，請輸入下列命令：  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     如果您只有自訂 `Binding` 型別，請輸入下列命令：  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     命令會產生 `BindingElement` 所需的三個 .cs 檔案 (如果指定 /be: 選項)、標準 `Binding` 所需的五個 .cs 檔案 (如果指定 /sb: 選項) 以及 .xml 檔案。  
  
    1. 如果使用 /be 選項，則其中一個 .cs 檔案會為您的繫結項目實作 `BindingElementExtensionSection`。 這個程式碼會公開 `BindingElement` 給組態系統，讓其他自訂繫結程序可以使用您的繫結程序項目。 其他檔案含有表示預設值和常數的類別。 檔案中會有 `//TODO` 註解，用意在提醒您更新預設值。  
  
    2. 如果您指定 /sb 選項，其中兩個 .cs 檔案將會分別實作 `StandardBindingElement` 和 `StandardBindingCollectionElement`，藉以向組態系統公開您的標準繫結。 其他檔案含有表示預設值和常數的類別。 檔案中會有 `//TODO` 註解，用意在提醒您更新預設值。  
  
         如果指定 /sb： 選項 Codetoaddto<\<*YourStdBinding*>.cs 中會有程式碼，您必須手動新增至實作標準繫結的類別。  
  
     SampleConfig.xml 檔案中含有組態程式碼，您必須將它新增至註冊處理常式 (在前面步驟 1 或 2 中定義) 的組態檔中。  
