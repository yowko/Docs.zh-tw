---
title: 作法：使用 DEVPATH 找出組件
description: 使用 XML 電腦設定檔和 DEVPATH 環境變數，測試共用元件是否可在 .NET 中的許多應用程式中正確運作。
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 8ae807e46b11d2adb06d6af0c86e1c7297caa0c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161980"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>作法：使用 DEVPATH 找出組件

開發人員可能會想要確保其所建立的共用元件能正確地搭配多個應用程式運作。 開發人員可以建立指向元件之組建輸出目錄的 DEVPATH 環境變數，而不是在開發週期期間持續將元件放在全域組件快取中。  
  
 例如，假設您正在建立名為 MySharedAssembly 的共用元件，而輸出目錄為 C:\MySharedAssembly\Debug。 您可以將 C:\MySharedAssembly\Debug 放在 DEVPATH 變數中。 然後，您必須 [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) 在電腦設定檔中指定元素。 這個元素會告知 common language runtime 使用 DEVPATH 來找出元件。  
  
 執行時間必須可探索共用的元件。  若要指定用來解析元件參考的私用目錄，請使用設定檔中的[ \<codeBase> 元素](./file-schema/runtime/codebase-element.md) [ \<probing> 或專案](./file-schema/runtime/probing-element.md)，如[指定元件的位置](specify-assembly-location.md)所述。  您也可以將元件放在應用程式目錄的子目錄中。 如需詳細資訊，請參閱 [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)。  
  
> [!NOTE]
> 這是一項先進的功能，僅供開發之用。  
  
 下列範例示範如何使執行時間搜尋 DEVPATH 環境變數所指定之目錄中的元件。  
  
## <a name="example"></a>範例  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 此設定預設為 false。  
  
> [!NOTE]
> 請只在開發階段使用此設定。 執行時間不會檢查在 DEVPATH 中找到之強式名稱元件的版本。 它只會使用它所找到的第一個元件。  
  
## <a name="see-also"></a>另請參閱

- [使用組態檔設定應用程式](index.md)
