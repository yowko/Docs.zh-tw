---
title: 建立模型和對應
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 133539ab1b6d6f2f0ab3f8deed5b22240c2bb07e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854399"
---
# <a name="modeling-and-mapping"></a>建立模型和對應
在 Entity Framework 中，您可以定義概念模型、儲存體模型，以及這兩者之間的對應，這兩種方式最適合您的應用程式。 Visual Studio 中的實體資料模型工具可讓您建立。來自資料庫或圖形化模型的[edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))檔案，然後在資料庫或模型變更時更新該檔案。  
  
 從 Entity Framework 4.1 開始，您也可以使用 Code First 開發透過程式設計方式建立模型。 Code First 開發有兩種不同的方案。 在這兩種情況下，開發人員透過編碼 .NET Framework 類別定義建立模型，然後選擇性地使用資料註解或 Fluent 應用程式開發介面指定其他對應或組態。  
  
 如需詳細資訊，請參閱[建立和對應概念模型](https://go.microsoft.com/fwlink/?LinkId=235016)。  
  
 您也可以使用包含在 .NET Framework 中的 EDM 產生器。 EdmGen.exe 可從現有的資料來源產生 .csdl、.ssdl 和 .msl 檔。 您也可以手動建立模型和對應內容。 如需詳細資訊，請參閱 EDM 產生器[（edmgen.exe .exe）](edm-generator-edmgen-exe.md)。
