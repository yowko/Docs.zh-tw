---
title: -errorreport
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dc321f7f927d68a9f270076640cbc6d31d2f6d5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="-errorreport"></a>-errorreport
指定 Visual Basic 編譯器報告編譯器內部錯誤的方式。  
  
## <a name="syntax"></a>語法  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>備註  
 此選項會提供便利的方式來報告 Visual Basic 編譯器內部錯誤 (ICE) 至 Microsoft 的 Visual Basic 小組。 根據預設，編譯器會將任何資訊傳送給 Microsoft。 不過，如果發生編譯器內部錯誤，此選項可讓您向 Microsoft 回報錯誤。 該資訊可協助 Microsoft 工程師找出原因，而且可能有助於改善 Visual Basic 中的下一個版本。  
  
 傳送報表的使用者的能力取決於電腦和使用者原則的權限。  
  
 下表摘要說明的效果`-errorreport`選項。  
  
|選項|行為|  
|---|---|  
|`prompt`|如果發生編譯器內部錯誤，對話方塊隨即出現，讓您可以檢視完全編譯器所收集的資料。 您可以判斷是否有任何錯誤報表中的機密資訊，並決定是否要傳送給 Microsoft。 如果您決定要傳送，而且電腦和使用者原則設定可讓它，編譯器會將資料傳送給 Microsoft。|  
|`queue`|佇列錯誤報告。 當您登入系統管理員權限時，您可以在上次登入報告任何失敗 （您不會提示要傳送報告的失敗一次以上每隔三天）。 這是預設行為時`-errorreport`未指定選項。|  
|`send`|如果發生編譯器內部錯誤，而且電腦和使用者原則設定可讓它，編譯器會將資料傳送給 Microsoft。<br /><br /> 選項`-errorreport:send`嘗試自動將錯誤資訊傳送給 Microsoft。 此選項取決於登錄中。 如需有關如何設定登錄中的適當值的詳細資訊，請參閱[如何開啟 Visual Studio 2008 命令列工具中的自動錯誤報告](http://go.microsoft.com/fwlink/?LinkID=184695)。|  
|`none`|如果發生編譯器內部錯誤，它將不會收集或傳送到 Microsoft。|  
  
 編譯器會傳送資料，包括堆疊時的錯誤，通常包含一些原始程式碼。 如果`-errorreport`搭配[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，則會傳送整個原始程式檔。  
  
 這個選項最適合搭配[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，因為它可讓 Microsoft 工程師更輕鬆地重現錯誤。  
  
> [!NOTE]
>  `-errorreport`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="example"></a>範例  
 下列程式碼會嘗試編譯`T2.vb`，和如果編譯器發生編譯器內部錯誤時，它會提示您傳送錯誤報表給 Microsoft。  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
