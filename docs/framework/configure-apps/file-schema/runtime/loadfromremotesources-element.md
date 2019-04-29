---
title: <loadFromRemoteSources> 項目
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568129f30267b212737ec8aa688cf882e19bbff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704592"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources > 項目
指定是否從遠端來源載入的組件，應該就會具有完全信任，在.NET Framework 4 和更新版本。
  
> [!NOTE]
>  如果您因為 Visual Studio 專案的錯誤清單或建置錯誤中的錯誤訊息導向這篇文章，請參閱[How to:使用 Visual Studio 中的 從 Web 組件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))。  
  
 \<configuration>  
\<執行階段 >  
\<loadFromRemoteSources>  
  
## <a name="syntax"></a>語法  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否會從遠端來源載入的組件，應該就會具有完全信任。|  
  
## <a name="enabled-attribute"></a>啟用的屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|請勿授與完全信任應用程式從遠端來源。 這是預設值。|  
|`true`|授與完全信任應用程式從遠端來源。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註

在.NET Framework 3.5 和更早版本中，如果您從遠端位置，載入組件的組件中的程式碼將取決於從其載入該區域的授權集的部分信任中執行。 比方說，如果您從網站載入組件，它會載入 [網際網路] 區域，並授與網際網路權限集合。 換句話說，它在網際網路沙箱中執行。

從.NET Framework 4 開始，程式碼存取安全性 (CAS) 原則已停用，並已載入以完全信任組件。 一般情況下，這會授與完全信任組件載入<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>先前已沙箱化的方法。 若要避免這個問題，預設會停用從遠端來源載入的組件中執行程式碼的能力。 根據預設，如果您嘗試載入遠端組件，<xref:System.IO.FileLoadException>像就會擲回下列例外狀況訊息：

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

若要載入的組件，並執行其程式碼，您必須使用下列其中一個：

- 組件明確建立沙箱 (請參閱[How to:在沙箱中執行部分信任程式碼](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md))。

- 以完全信任執行組件的程式碼。 您可以設定`<loadFromRemoteSources>`項目。 它可讓您指定在舊版.NET Framework 中的部分信任中執行的組件現在在.NET Framework 4 及更新版本中的完全信任中執行。

> [!IMPORTANT]
> 如果組件不應在完全信任中執行，不會設定這個組態項目。 反而是建立沙箱<xref:System.AppDomain>要載入的組件。

`enabled`屬性`<loadFromRemoteSources>`項目是有效僅當程式碼存取安全性 (CAS) 已停用。 根據預設，已停用在.NET Framework 4 和更新版本的 CAS 原則。 如果您設定`enabled`至`true`，遠端組件都會授予完全信任。

如果`enabled`未設為`true`、<xref:System.IO.FileLoadException>在任一個下列條件時會擲回：

- 目前的沙箱行為是網域的不同於其行為在.NET Framework 3.5。 這需要停用時，CAS 原則和目前網域不受限於沙箱。

- 正在載入的組件不是來自`MyComputer`區域。

設定`<loadFromRemoteSources>`項目`true`可避免擲回這個例外狀況。 它可讓您指定，您可以不依賴沙箱的 common language runtime 載入的組件的安全性，以及它們可以允許在執行完全信任。

## <a name="notes"></a>注意

- 在.NET Framework 4.5 和更新版本中，區域網路共用上的組件以完全信任執行的預設值;您沒有啟用`<loadFromRemoteSources>`項目。

- 如果已從網路複製應用程式，即使該應用程式位於本機電腦上，Windows 仍會將它標示為 Web 應用程式。 您可以藉由變更其檔案屬性，變更該名稱，或者您可以使用`<loadFromRemoteSources>`授與組件的項目完全信任。 或者，您可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法載入作業系統標示為從 Web 載入的本機組件。

- 您可能會收到<xref:System.IO.FileLoadException>Windows Virtual PC 應用程式中執行的應用程式中。 當您嘗試從主機服務電腦上的連結資料夾載入檔案時，也可會發生。 它也可能發生於您嘗試從透過連結的資料夾載入檔案[Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services)。 若要避免例外狀況，請設定`enabled`至`true`。

## <a name="configuration-file"></a>組態檔

此項目通常用於應用程式組態檔，不過可以根據內容用於其他組態檔。 如需詳細資訊，請參閱文章[更多隱含的 CAS 原則用法： loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) .NET Security 部落格中。  

## <a name="example"></a>範例

下列範例示範如何從遠端來源載入的組件授與完全信任。

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>另請參閱

- [更為隱含的 CAS 原則用法： loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [如何：在沙箱中執行部分信任的程式碼](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
