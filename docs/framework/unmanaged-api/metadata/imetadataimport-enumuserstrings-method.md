---
title: "IMetaDataImport::EnumUserStrings 메서드"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUserStrings
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 48ec44d993c5cdc2c545125bf8b4bcb80e413f95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumuserstrings-method"></a>IMetaDataImport::EnumUserStrings 메서드
현재 메타데이터 범위에서 하드 코드된 문자열을 나타내는 String 토큰을 열거합니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `phEnum`  
 [out에서] 열거자에 대 한 포인터입니다. 이 메서드의 첫 번째 호출에 대 한 NULL 이어야 합니다.  
  
 `rStrings`  
 [out] 문자열 토큰을 저장 하는 데 사용 되는 배열입니다.  
  
 `cMax`  
 [in] `rStrings` 배열의 최대 크기입니다.  
  
 `pcStrings`  
 [out] 반환 된 문자열 토큰 수 `rStrings`합니다.  
  
## <a name="return-value"></a>반환 값  
  
|HRESULT|설명|  
|-------------|-----------------|  
|`S_OK`|`EnumUserStrings`성공적으로 반환 합니다.|  
|`S_FALSE`|열거할 토큰이 있습니다. 이 경우 `pcStrings` 은 0입니다.|  
  
## <a name="remarks"></a>설명  
 String 토큰에 의해 만들어집니다는 [imetadataemit:: Defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) 메서드. 이 메서드는 컴파일러에서가 아니라 메타 데이터 브라우저에서 사용 될 디자인 되었습니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.  
  
 **헤더:** Cor.h  
  
 **라이브러리:** MsCorEE.dll에 리소스로 포함  
  
 **.NET framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [IMetaDataImport 인터페이스](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 인터페이스](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
