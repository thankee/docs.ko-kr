---
title: "EmitManifest 메서드"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitManifest
- IALink.EmitManifest
api_location: alink.dll
api_type: COM
f1_keywords: EmitManifest
helpviewer_keywords: EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 03ef815f03a65cbf7e2dc936b21848e206132add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="emitmanifest-method"></a><span data-ttu-id="64116-102">EmitManifest 메서드</span><span class="sxs-lookup"><span data-stu-id="64116-102">EmitManifest Method</span></span>
<span data-ttu-id="64116-103">최종 매니페스트를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="64116-103">Emits the final manifest.</span></span> <span data-ttu-id="64116-104">다른 모든 파일을 가져오면 모든 옵션을 설정한 후이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="64116-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="64116-105">바인딩되지 않은 모듈에 대 한이 메서드를 호출 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="64116-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64116-106">구문</span><span class="sxs-lookup"><span data-stu-id="64116-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64116-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="64116-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="64116-108">어셈블리의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="64116-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="64116-109">검색 된 어셈블리 파일에 예약 하 고 크기를 받는 [StrongNameSignatureSize 함수](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="64116-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="64116-110">필요에 따라 어셈블리 매니페스트 토큰을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="64116-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64116-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="64116-111">Return Value</span></span>  
 <span data-ttu-id="64116-112">메서드가 성공 하면 S_OK를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="64116-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64116-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="64116-113">Requirements</span></span>  
 <span data-ttu-id="64116-114">Alink.h가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="64116-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64116-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64116-115">See Also</span></span>  
 [<span data-ttu-id="64116-116">IALink 인터페이스</span><span class="sxs-lookup"><span data-stu-id="64116-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="64116-117">IALink2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="64116-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="64116-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="64116-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)