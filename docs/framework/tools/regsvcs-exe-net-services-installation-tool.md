---
title: "Regsvcs.exe (.NET 服務安裝工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfe7c3e34c2ceaf01f89c1e54f930991ee7e0a2b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (.NET 服務安裝工具)
.NET 服務安裝工具會執行下列動作：  
  
-   載入和註冊組件。  
  
-   產生、註冊和安裝類型程式庫到指定的 COM+ 應用程式。  
  
-   設定您以程式設計方式加入至類別的服務。  
  
 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
#### <a name="parameters"></a>參數  
  
|引數|描述|  
|--------------|-----------------|  
|*assemblyFile.dll*|來源組件檔。 這個組件必須以強式名稱簽署。 如需詳細資訊，請參閱[以強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。|  
  
|選項|描述|  
|------------|-----------------|  
|**/appdir:<路徑>** |指定應用程式的根目錄。|  
|**/appname:<應用程式名稱>** |指定要尋找或建立之 COM+ 應用程式的名稱。|  
|**/c**|建立目標應用程式。|  
|**/componly**|只設定元件，忽略方法和介面。|  
|**/exapp**|指定需要現有應用程式的工具。|  
|**/extlb**|使用現有的類型程式庫。|  
|**/fc**|尋找或建立目標應用程式。|  
|**/help**|顯示工具的命令語法和選項。|  
|**/noreconfig**|不要重新設定現有的目標應用程式。|  
|**/nologo**|隱藏 Microsoft 程式啟始資訊顯示。|  
|**/parname:** *name*|指定要尋找或建立之 COM+ 應用程式的名稱或 ID。|  
|**/reconfig**|重新設定現有的目標應用程式。 這是預設值。|  
|**/tlb:<型別程式庫檔案>** |指定要安裝的類型程式庫檔案。|  
|**/u**|解除安裝目標應用程式。|  
|**/quiet**|指定安靜模式，隱藏標誌或成功訊息顯示。|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 Regsvcs.exe 需要由 *assemblyFile.dll* 所指定的來源組件檔。 這個組件必須使用強式名稱簽署。 如需強式名稱簽署的詳細資訊，請參閱[以強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。 目標應用程式和類型程式庫檔案的名稱是選擇項。 如果 *applicationName* 引數已經不存在，則可以從來源組件檔中產生，並且將會由 Regsvcs.exe 建立。 *typelibraryfile* 引數可以指定型別程式庫名稱。 如果您沒有指定類型程式庫名稱，Regsvcs.exe 會使用組件名稱做為預設值。  
  
 當 Regsvcs.exe 註冊元件的方法時，它會受制於這些方法上的[要求](http://msdn.microsoft.com/library/e5283e28-2366-4519-b27d-ef5c1ddc1f48)和[連結要求](../../../docs/framework/misc/link-demands.md)。 因為這個工具是在完全信任的環境中執行，所以大部分的使用權限需求都會成功。 不過，Regsvcs.exe 無法註冊方法受到 <xref:System.Security.Permissions.StrongNameIdentityPermission> 或 <xref:System.Security.Permissions.PublisherIdentityPermission> 的需求或連結要求保護的元件。  
  
 您必須擁有本機電腦上的系統管理員權限，才能使用 Regsvcs.exe。  
  
 在執行任何這些動作時，如果 Regsvcs.exe 失敗，會顯示對應的錯誤訊息。  
  
## <a name="examples"></a>範例  
 下列命令會將 `myTest.dll` 中包含的所有公用類別加入 `myTargetApp` (現有的 COM+ 應用程式)，並產生 `myTest.tlb` 類型程式庫。  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 下列命令會將 `myTest.dll` 中包含的所有公用類別加入 `myTargetApp` (現有的 COM+ 應用程式)，並產生 `newTest.tlb` 類型程式庫。  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>請參閱  
 [工具](../../../docs/framework/tools/index.md)  
 [如何：使用強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
