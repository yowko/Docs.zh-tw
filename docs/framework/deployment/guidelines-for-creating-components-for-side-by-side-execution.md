---
title: 建立並存執行元件的方針
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f45e68d9d340d857bc25b3848bd687e46fd73c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>建立並存執行元件的方針
請遵循這些一般方針建立為並存執行而設計的 Managed 應用程式或元件：  
  
-   將類型識別繫結至特定版本的檔案。  
  
     Common Language Runtime 會使用強式名稱的組件，將類型識別繫結到特定的檔案版本。 若要建立用於並存執行的應用程式或元件，您必須為所有組件指定強式名稱。 這會建立精確的類型識別，並確保將任何的類型解析導向到正確的檔案。 強式名稱的組件包含版本、文化特性和發行者資訊，可供執行階段找出符合繫結要求的正確檔案。  
  
-   使用版本感知儲存區。  
  
     此執行階段使用全域組件快取提供版本感知儲存區。 全域組件快取是一種版本感知目錄結構，安裝在使用 .NET Framework 的每一台電腦上。 安裝在全域組件快取的組件不會在安裝該組件新版本時被覆寫。  
  
-   建立在隔離狀態執行的應用程式或元件。  
  
     在隔離狀態執行的應用程式或元件必須管理資源，以避免該應用程式或元件的兩個執行個體同時執行時產生衝突。 應用程式或元件也必須使用版本特定的檔案結構。  
  
## <a name="application-and-component-isolation"></a>應用程式和元件隔離  
 隔離是成功設計用於並存執行之應用程式或元件的其中一個關鍵。 應用程式或元件必須以隔離的方式管理所有資源，尤其是檔案 I/O。 請遵循這些方針，確定您的應用程式或元件在隔離狀態執行：  
  
-   以版本特定的方式寫入登錄。 將值儲存在指出此版本的登錄區或機碼中，且不要在各種版本的元件之間共用資訊或狀態。 這可防止同時執行的兩個應用程式或元件覆寫資訊。  
  
-   使具名的核心物件變成版本特定的物件，讓競爭情形不要發生。 例如，當相同應用程式之兩個版本的兩個信號互相等候時就會發生競爭情形。  
  
-   將檔案和目錄名稱變成版本感知的名稱。 這表示檔案結構應該要依賴版本資訊。  
  
-   使用版本特定的方式建立帳戶和群組。 應用程式所建立的使用者帳戶和群組應該以版本識別。 請勿在應用程式版本之間共用使用者帳戶和群組。  
  
## <a name="installing-and-uninstalling-versions"></a>安裝和解除安裝版本  
 設定用於並存執行的應用程式時，請遵循這些有關安裝及解除安裝版本的方針：  
  
-   請勿從登錄中刪除資訊；其他應用程式在不同版本的 .NET Framework 下執行時可能需要用到這些資訊。  
  
-   請勿取代登錄中的資訊；其他應用程式在不同版本的 .NET Framework 下執行時可能需要用到這些資訊。  
  
-   請勿移除註冊 COM 元件；其他應用程式在不同版本的 .NET Framework 下執行時可能需要用到這些資訊。  
  
-   請勿變更 **InprocServer32** 或已登錄的 COM 伺服器的其他登錄項目。  
  
-   請勿刪除使用者帳戶或群組；其他應用程式在不同版本的 .NET Framework 下執行時可能需要用到這些資訊。  
  
-   請勿將任何項目加入包含未建立版本之路徑的登錄。  
  
## <a name="file-version-number-and-assembly-version-number"></a>檔案版本號碼和組件版本號碼  
 檔案版本是執行階段不使用的 Win32 版本資源。 一般來說，您甚至可以就地更新檔案版本。 兩個相同的檔案可以有不同的檔案版本資訊，而兩個不同的檔案也可以有相同的檔案版本資訊。  
  
 組件版本可供執行階段用於組件繫結。 執行階段會將兩個具有不同版本號碼的相同組件視為兩個不同的組件。  
  
 當只有檔案版本號碼是新的時，[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 可讓您替換組件。 除非組件版本號碼比較高，否則安裝程式通常不會在組件上執行覆寫安裝。  
  
## <a name="see-also"></a>請參閱  
 [並存執行](../../../docs/framework/deployment/side-by-side-execution.md)  
 [如何：啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
