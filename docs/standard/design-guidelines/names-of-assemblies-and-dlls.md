---
title: 組件和 DLL 的名稱
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: KrzysztofCwalina
ms.openlocfilehash: 1aeef9e1be6e5fe747f440a8cb7f21095cb22f49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945492"
---
# <a name="names-of-assemblies-and-dlls"></a>組件和 DLL 的名稱
組件是部署和 managed 程式碼程式的身分識別的單位。 雖然組件可以跨越一或多個檔案，通常對應一對一與 DLL 組件。 因此，本節會描述唯一 DLL 命名慣例，則可以對應至組件命名慣例。  
  
 **✓ DO** 選擇的組件提供建議的功能，例如 System.Data 大型區塊的 Dll 名稱。  
  
 組件和 DLL 的名稱不一定要對應至命名空間名稱，但很合理地命名組件時，請遵循此命名空間名稱。 好的經驗法則是命名為基礎的共同首碼的組件中包含的命名空間的 DLL。 比方說，有兩個命名空間，組件`MyCompany.MyTechnology.FirstFeature`並`MyCompany.MyTechnology.SecondFeature`，可能會呼叫`MyCompany.MyTechnology.dll`。  
  
 **✓ CONSIDER** 命名 Dll 根據下列模式：  
  
 `<Company>.<Component>.dll`  
  
 其中`<Component>`包含一或多個點分隔的子句。 例如:   
  
 `Litware.Controls.dll`.  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
