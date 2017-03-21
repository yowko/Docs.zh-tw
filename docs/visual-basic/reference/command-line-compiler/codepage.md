---
title: "/codepage (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 90dce6e34e52862807e2acdbf1850699316730d1
ms.lasthandoff: 03/13/2017

---
# <a name="codepage-visual-basic"></a>/codepage (Visual Basic)
指定編譯過程中所有原始程式碼檔使用的字碼頁。  
  
## <a name="syntax"></a>語法  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`id`|必要項。 編譯器會使用所指定的字碼頁`id`解譯原始程式檔的編碼方式。|  
  
## <a name="remarks"></a>備註  
 若要編譯原始程式碼與特定的編碼方式儲存，您可以使用`/codepage`來指定應該使用的字碼頁。 `/codepage`選項套用至所有您所編譯的原始程式碼檔案。 如需詳細資訊，請參閱[.NET Framework 中的字元編碼](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)。  
  
 `/codepage`選項不需要簽章中使用目前的 ANSI 字碼頁、 Unicode 或 utf-8 格式儲存的原始程式碼檔案。 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]儲存所有原始程式碼檔案與目前的 ANSI 字碼頁，根據預設，除非使用者指定另一個編碼**編碼**對話方塊。 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]使用**編碼**對話方塊來開啟不同的字碼頁所儲存的原始程式碼檔。  
  
> [!NOTE]
>  `/codepage`選項不可以從[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]開發環境，它才可使用從命令列進行編譯。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
