---
title: 此單一執行個體應用程式無法連接到原始執行個體
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 7ffa9b185e16cfdf8223ce84e77d1a0e1fa67f65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322650"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>此單一執行個體應用程式無法連接到原始執行個體
此單一執行個體應用程式無法連接到原始執行個體。 此問題的部分可能原因如下：  
  
-   原始執行個體停止回應。  
  
-   應用程式沒有建立核心物件的權限。 如需有關核心物件的詳細資訊，請參閱 < [Mutex](../../standard/threading/mutexes.md)。  
  
     核心物件的主檔名 (Base Name) 是由連接組件的 GUID、主要版本號碼，以及次要版本號碼所組成。 例如，基底名稱可能是 `3639f15d-9547-43da-8145-60da347829915.1`。  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>在開發應用程式時更正這個錯誤  
  
1. 檢查應用程式並未進入沒有回應的狀態。  
  
2. 檢查應用程式有足夠的權限可建立核心物件。  
  
3. 重新啟動應用程式的原始執行個體。  
  
4. 重新啟動電腦，以針對連接到原始執行個體應用程式所需的資源，清除可能正在使用它的任何處理序。  
  
5. 記下錯誤發生時的情況，並致電 Microsoft 產品支援服務。  
  
## <a name="see-also"></a>另請參閱

- [偵錯工具基礎](/visualstudio/debugger/debugger-basics)
