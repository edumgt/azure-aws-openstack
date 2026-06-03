# ☁️ OpenStack Private Cloud Labs

> OpenStack 핵심 리소스 중심의 프라이빗 클라우드 설계/운영 가이드

---

## 📚 OpenStack 리소스 구성

| 리소스 | 서비스 | 주요 기능 | 활용 예시 |
|--------|--------|-----------|-----------|
| Compute | Nova | VM 생성, 하이퍼바이저 스케줄링, 인스턴스 수명주기 관리 | 업무 시스템용 가상 서버 풀 구성 |
| Networking | Neutron | 네트워크 세그먼트, 라우터, DHCP, 보안그룹, Floating IP | 내부망/DMZ 분리, 외부 노출 서비스 구성 |
| Block Storage | Cinder | VM 연결형 영구 볼륨, 스냅샷, 백업 | DB 서버용 고가용성 스토리지 |
| Object Storage | Swift | 오브젝트 저장, 복제, 대규모 아카이브 | 로그/백업 파일 장기 보관 |
| Image | Glance | OS/애플리케이션 이미지 등록, 버전 관리, 배포 | 표준 VM 이미지 카탈로그 운영 |
| Identity | Keystone | 인증/인가, 프로젝트/테넌트, 역할 관리 | 조직 단위 멀티테넌시 권한 정책 |
| Dashboard | Horizon | 웹 콘솔 기반 리소스 관리/모니터링 | 운영팀 셀프서비스 포털 |
| Orchestration | Heat | 템플릿 기반 인프라 배포, 스택 관리 | IaC 기반 표준 환경 자동 구축 |
| Telemetry | Ceilometer / Aodh | 사용량 수집, 이벤트/알람 | 용량 계획, 비용/리소스 모니터링 |

---

## 🏗️ OpenStack 아키텍처 관점 핵심 포인트

1. **컨트롤 플레인 고가용성**: Keystone, Neutron, Glance API 다중화 및 DB/메시지큐 이중화
2. **컴퓨트 확장성**: Nova Compute 노드 수평 확장 + 가상화 자원 풀 운영
3. **스토리지 전략**: Cinder(블록)와 Swift(오브젝트) 역할 분리, 백업/아카이브 정책 표준화
4. **보안/거버넌스**: 프로젝트 단위 RBAC, 네트워크 마이크로세그멘테이션, 감사 로그 체계화
5. **자동화 운영**: Heat 템플릿, Ansible/Terraform 연계로 구축·변경 표준화
