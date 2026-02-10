"# ROS2 (Robot Operating System 2)

## 개요
ROS2는 로봇 소프트웨어 개발을 위한 차세대 오픈소스 프레임워크입니다. ROS1의 경험을 바탕으로 실시간성, 보안성, 그리고 상용화 요구사항을 충족하도록 처음부터 다시 설계되었습니다.

## 주요 특징

### 🚀 실시간 지원
- DDS(Data Distribution Service) 기반 통신
- 결정론적 동작을 위한 실시간 제어 지원
- 우선순위 기반 스케줄링

### 🔒 보안
- DDS Security를 통한 인증 및 암호화
- 접근 제어 및 권한 관리
- 보안 통신 채널

### 🌐 멀티 플랫폼
- Linux, Windows, macOS 지원
- 임베디드 시스템 지원
- 다양한 아키텍처 호환

### 🤝 표준 기반
- OMG DDS 표준 사용
- 벤더 독립적인 통신
- 다양한 DDS 구현체 선택 가능

## 아키텍처

ROS2는 계층화된 아키텍처를 채택합니다:

1. **OS Layer**: 운영체제 추상화
2. **RMW Layer**: ROS Middleware 인터페이스
3. **DDS Layer**: 실제 통신 구현
4. **Client Libraries**: rclcpp (C++), rclpy (Python)

## 핵심 개념

### Node (노드)
독립적인 실행 단위로, 특정 작업을 수행하는 프로세스

### Topic (토픽)
비동기식 메시지 기반 통신 방식 (Publish-Subscribe)

### Service (서비스)
동기식 요청-응답 통신 방식

### Action (액션)
장기 실행 작업을 위한 비동기 요청-응답 통신

### Parameter (파라미터)
노드의 동적 설정 값

## ROS1과의 차이점

| 항목 | ROS1 | ROS2 |
|------|------|------|
| 통신 | Custom TCP/UDP | DDS |
| 실시간성 | 제한적 | 완전 지원 |
| 보안 | 미흡 | DDS Security |
| 플랫폼 | 주로 Linux | 멀티 플랫폼 |
| Master | 중앙집중식 | 분산형 |

## 지원 버전

- **Foxy Fitzroy** (LTS) - Ubuntu 20.04
- **Galactic Geochelone** - Ubuntu 20.04
- **Humble Hawksbill** (LTS) - Ubuntu 22.04
- **Iron Irwini** - Ubuntu 22.04
- **Jazzy Jalisco** (LTS) - Ubuntu 24.04

## 시작하기

### 설치
```bash
# Ubuntu 22.04 기준 (Humble)
sudo apt update
sudo apt install ros-humble-desktop
```

### 환경 설정
```bash
source /opt/ros/humble/setup.bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```

### 간단한 예제
```python
# Python Publisher
import rclpy
from rclpy.node import Node
from std_msgs.msg import String

class MinimalPublisher(Node):
    def __init__(self):
        super().__init__('minimal_publisher')
        self.publisher_ = self.create_publisher(String, 'topic', 10)
        self.timer = self.create_timer(0.5, self.timer_callback)
        
    def timer_callback(self):
        msg = String()
        msg.data = 'Hello ROS2!'
        self.publisher_.publish(msg)

def main(args=None):
    rclpy.init(args=args)
    node = MinimalPublisher()
    rclpy.spin(node)
    node.destroy_node()
    rclpy.shutdown()
```

## 활용 분야

- 🤖 서비스 로봇
- 🚗 자율주행 차량
- 🏭 산업용 로봇
- 🚁 드론 및 UAV
- 🦾 협동 로봇 (Cobot)

## 주요 도구

- **RViz2**: 3D 시각화 도구
- **rqt**: Qt 기반 GUI 도구 모음
- **Gazebo**: 로봇 시뮬레이터
- **ros2bag**: 데이터 기록 및 재생
- **Colcon**: 빌드 도구

## 커뮤니티 및 리소스

- 📚 공식 문서: [docs.ros.org](https://docs.ros.org)
- 💬 Discourse: [discourse.ros.org](https://discourse.ros.org)
- 📦 패키지 인덱스: [index.ros.org](https://index.ros.org)
- 🐙 GitHub: [github.com/ros2](https://github.com/ros2)

## 라이선스

ROS2는 Apache 2.0 라이선스로 배포되어 상용 및 비상용 프로젝트 모두에서 자유롭게 사용할 수 있습니다.

---

**ROS2로 로봇 개발을 시작해보세요! 🚀**" 
