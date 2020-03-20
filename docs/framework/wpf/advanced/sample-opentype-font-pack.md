---
title: 範例 OpenType 字型套件
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 30cb69fcf05108822e8f3e2d45c9e79dbced26ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181903"
---
# <a name="sample-opentype-font-pack"></a>範例 OpenType 字型套件
本主題概述了隨 Windows SDK 一起分發的示例 OpenType 字型。 示例字體支援應用程式可以使用的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]擴展 OpenType 功能。  

<a name="overview"></a>
## <a name="fonts-in-the-opentype-font-pack"></a>OpenType 字型套件中的字型  
 Windows SDK 提供了一組示例 OpenType 字型，可用於創建[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式。 範例字型是根據 Ascender Corporation 的授權來提供。 這些字體僅實現 OpenType 格式定義的總功能的子集。 下表列出了示例 OpenType 字型的名稱。  
  
|**名稱**|**檔案**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 下圖顯示了示例 OpenType 字型的外觀。  
  
 ![列出範例字型套件中的字型名稱](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 範例字型是根據 Ascender Corporation 的授權來提供。 Ascender 是進階字型產品的供應商。 若要授權範例字型的延伸或自訂版本，請參閱 [Ascender Corporation 網站 (英文)](https://www.monotype.com/)。  
  
> [!NOTE]
> 身為開發人員，您的職責是確保對於您內嵌在應用程式中或是以其他方式轉散發的任何字型，您必須有必要的授權權限。  
  
<a name="installing_the_fonts"></a>
## <a name="installing-the-fonts"></a>安裝字型  
 您可以選擇將示例 OpenType 字型安裝到預設的 Windows 字體目錄 **[WINDOWS]字體**。 使用 [字型] 控制台來安裝字型。 這些字體在電腦上後，引用預設 Windows 字體的所有應用程式都可以訪問這些字體。 您可以按兩下字型檔案，以數個字型大小來顯示一組代表字元。 下列螢幕擷取畫面顯示 Lindsey 字型檔案 Linds.ttf。  
  
 ![Lindsey 字型 &#40;OpenType&#41;](./media/typographyinwpf-04.png "TypographyInWPF_04")  
顯示 Lindsey 字型  
  
<a name="using_the_fonts"></a>
## <a name="using-the-fonts"></a>使用字型  
 有兩種方式可讓您在應用程式中使用字型。 您可將字型新增到您的應用程式以做為專案內容項目，此項目並未內嵌為組件中的資源。 或者，您可以將字型新增到您的應用程式，以做為內嵌於您應用程式組件檔中的專案資源項目。 如需詳細資訊，請參閱[將字型與應用程式一起封裝](packaging-fonts-with-applications.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Documents.Typography>
- [OpenType 字型功能](opentype-font-features.md)
- [將字型與應用程式一起封裝](packaging-fonts-with-applications.md)
