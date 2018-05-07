---
title: 組件和 DLL 的名稱
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6cf175472d68e99598dd56e170bee3d37ae3c2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="names-of-assemblies-and-dlls"></a>組件和 DLL 的名稱
組件是部署和 managed 程式碼程式的身分識別的單位。 雖然組件可以跨一個或多個檔案，通常是組件以一對一對應的 DLL。 因此，本節會說明只 DLL 命名慣例，然後可以對應至組件命名慣例。  
  
 **✓ 不要**選擇的組件提供建議的功能，例如 System.Data 大型區塊的 Dll 名稱。  
  
 組件和 DLL 名稱沒有對應至命名空間名稱，但是很合理命名組件時所應遵循的命名空間名稱。 最佳經驗法則是名稱的組件中包含的命名空間的一般前置詞為基礎的 DLL。 例如，兩個命名空間，與組件`MyCompany.MyTechnology.FirstFeature`和`MyCompany.MyTechnology.SecondFeature`，無法呼叫`MyCompany.MyTechnology.dll`。  
  
 **✓ 考慮**命名 Dll 根據下列模式：  
  
 `<Company>.<Component>.dll`  
  
 其中`<Component>`包含一或多個點分隔的子句。 例如:   
  
 `Litware.Controls.dll`.  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
