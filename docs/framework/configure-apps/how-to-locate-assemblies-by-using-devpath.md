---
title: 作法：使用 DEVPATH 找出組件
description: 使用 XML 電腦設定檔和 DEVPATH 環境變數，測試共用元件是否可在 .NET 中搭配許多應用程式正常運作。
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 50b61eedddabd660b1834565a61738f460ae9ff9
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105381"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>作法：使用 DEVPATH 找出組件
開發人員可能會想要確定它們所建立的共用元件能與多個應用程式正確搭配運作。 開發人員可以建立 DEVPATH 環境變數，以指向元件的組建輸出目錄，而不是在開發週期期間持續將元件放在全域組件快取中。  
  
 例如，假設您要建立一個名為 MySharedAssembly 的共用元件，而輸出目錄是 C:\MySharedAssembly\Debug。 您可以將 C:\MySharedAssembly\Debug 放在 DEVPATH 變數中。 接著，您必須 [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) 在電腦設定檔中指定元素。 這個元素會告知 common language runtime 使用 DEVPATH 來尋找元件。  
  
 執行時間必須可探索共用元件。  若要指定解析元件參考的私用目錄，請使用設定檔中的[ \<codeBase> 元素](./file-schema/runtime/codebase-element.md)或[ \<probing> 元素](./file-schema/runtime/probing-element.md)，如[指定元件的位置](specify-assembly-location.md)中所述。  您也可以將元件放在應用程式目錄的子目錄中。 如需詳細資訊，請參閱 [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)。  
  
> [!NOTE]
> 這是一項先進的功能，僅供開發之用。  
  
 下列範例顯示如何讓執行時間在 DEVPATH 環境變數所指定的目錄中搜尋元件。  
  
## <a name="example"></a>範例  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 此設定的預設值為 false。  
  
> [!NOTE]
> 請只在開發階段使用此設定。 執行時間不會檢查在 DEVPATH 中找到的強式名稱元件上的版本。 它只會使用所找到的第一個元件。  
  
## <a name="see-also"></a>另請參閱

- [使用組態檔設定應用程式](index.md)
