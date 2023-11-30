# OPERATING SYSTEM

1. [운영체제와 컴퓨터](https://polydactyl-impala-301.notion.site/f0c9f9c339654b318324ed9e6469a27f?pvs=4) - 주연

2. [메모리 계층 - 동민](https://www.notion.so/ehdals0405/75cd2b7e748f4c229388d7b51c69b020)

3. [프로세스와 스레드](https://polydactyl-impala-301.notion.site/fffebfb0df8841e3bca5027fc24bfeec?pvs=4) - 주연 

4. [CPU 스케줄링 알고리즘](https://flossy-longship-14b.notion.site/CPU-225df150fa444d2f8d470660dc82add9?pvs=4) - 솔이

5. [인터럽트(Interrupt)](https://www.notion.so/ehdals0405/3137965e1f754ecc8bca712bd7496f11)  - 동민

6. [시스템 콜(System Call)](https://flossy-longship-14b.notion.site/System-Call-6037e8e2283d4b76aed025ac7ed8927b?pvs=4) - 솔이

7. [PCB와 Context Switching - 동민](https://www.notion.so/ehdals0405/PCB-Context-Switching-496f2cd2a75e488fa754f1ebe3a6bc4e)

8. [주소 공간과 주소 변환(Address Space, Address Translation)](https://polydactyl-impala-301.notion.site/Address-Space-Address-Translation-c5193d250b8d4c26b337a50c5533e6e6?pvs=4) - 주연

9. [가상 메모리(Virtual Memory)](https://polydactyl-impala-301.notion.site/Virtual-Memory-c0eb3e0884d342a6bfad77d89c7b7039?pvs=4) - 주연

10. [세그먼테이션(Segmentation)](https://flossy-longship-14b.notion.site/Segmentation-3e1d4fe29f324e8e9d451beb58b50dff?pvs=4)  - 솔이

11. [페이징(Paging)](https://www.notion.so/ehdals0405/Paging-7a95433edf6b4d2789098686c9381658) - 동민

12. [가상메모리와 요구 페이징, 페이지 교체](https://flossy-longship-14b.notion.site/Segmentation-3e1d4fe29f324e8e9d451beb58b50dff?pvs=4)  - 솔이

13. [TLB(Translation Lookaside Buffers)](https://flossy-longship-14b.notion.site/TLB-Translation-Lookaside-Buffer-1394951c2e384f9a9f123039645f0cbb?pvs=4) - 솔이

14. [TLB 심화](https://flossy-longship-14b.notion.site/TLB-Translation-Lookaside-Buffers-ee889e8ebd73467c96ab8b804415d984?pvs=4) - 솔이

15. Paging : Smaller Table - 주연

16. [동기화(스핀락, 세마포어, 뮤텍스)](https://www.notion.so/ehdals0405/db0090550b0e40899e451ffbffb6a071) - 동민 

17. [교착상태(DeadLock)](https://www.notion.so/ehdals0405/Dead-Lock-4638a0064a524ffe9221012ba4fa376f) - 동민

18. 멀티프로세스, 스레드와 멀티스레딩 - 주연


<br/>

## 면접 질문 ❓
<details>
<summary>
프로세스와 스레드의 차이를 설명해보세요.
</summary>
<hr/>
💬 프로세스는 메모리 상에서 실행중인 프로그램을 말하며, 스레드는 프로세스 내에서 실행되는 흐름의 단위를 의미합니다.

프로세스는 독립된 주소공간인 stack, code, heap을 할당받으며 각 프로세스는 최소 하나의 스레드를 갖고 있습니다.

스레드는 stack 메모리만 할당 받고 나머지 code, heap 영역은 프로세스 내의 다른 스레드들과 공유합니다. 스레드는 프로세스보다 가볍고 자원을 공유하기 때문에 **문맥교환**이 더욱 빠르고 효율적입니다.
<br/>
</details>

<details>
<summary>
컨텍스트 스위칭에 대해 설명해보세요.
</summary>
<hr/>
  
💬 [🔗 참고자료](https://inpa.tistory.com/entry/%F0%9F%91%A9%E2%80%8D%F0%9F%92%BB-%EB%8F%99%EA%B8%B0%EB%B9%84%EB%8F%99%EA%B8%B0-%EB%B8%94%EB%A1%9C%ED%82%B9%EB%85%BC%EB%B8%94%EB%A1%9C%ED%82%B9-%EA%B0%9C%EB%85%90-%EC%A0%95%EB%A6%AC#%EB%8F%99%EA%B8%B0synchronous_/_%EB%B9%84%EB%8F%99%EA%B8%B0asynchronous)

동기, 비동기는 요청한 작업에 대해 완료 여부를 따져서 작업을 순차적으로 수행할지 아닌지를 나타내는 것이고 블로킹과 논블로킹은 현재 작업이 block(차단, 대기) 되느냐, 아니냐에 따라 다른 작업을 수행할 수 있는지에 대한 관점으로 내가 직접 제어할 수 없는 대상(IO/멀티스레드)을 상대하는 방법에 대한 분류를 나타냅니다.

**✅ 동기**

- 한 작업이 완료되기 전까지 다음 작업은 대기하기 때문에 순차적으로 실행됩니다.
- 순서가 명확하기 때문에 흐름을 이해하기 쉽습니다.
- 하지만, 한 작업이 끝날 때 까지 기다리는 동안 자원 활용이 비효율적일 수 있다는 단점이 있습니다.

**✅ 비동기**

- 한 작업이 완료되기 전에 다음 작업의 시작이 가능합니다.
- 자원 활용이 효율적이며 여러 작업을 동시에 처리할 수 있기 때문에 시스템의 처리량을 높일 수 있다는 장점이 있으며 대규모 트래픽에서도 안정적으로 동작할 수 있는 웹 애플리케이션을 만들 수 있습니다.
- 작업 간의 의존성이 복잡해질 수 있고 흐름의 관리가 어려워져서 프로그램의 디버깅이 어렵습니다.

**✅ 블로킹(Block)**

- 요청한 작업이 완료될 때 까지 기다렸다가 작업이 완료되면 다음 작업을 진행할 수 있는 것으로 제어권을 작업 대상이 가지고 있는 것을 말합니다.
- 작업의 완료를 보장하며 흐름 제어가 단순하다는 장점이 있지만 대기 동안 다른 작업을 수행할 수 없기 때문에 자원의 활용도가 낮을 수 있습니다.

**✅ 넌 블로킹(Non-Block)**

- 요청한 작업을 기다리지 않고 다른 작업을 즉시 시작하는 것입니다.
- 대기 상태 없이 지속적으로 작업 수행이 가능 하기 때문에 자원 활용도가 높지만 작업의 완료 상태를 주기적으로 확인해야 하기 때문에 관리가 번거로울 수 있습니다.
</aside>
<br/>
<br/>
</details>

<details>
<summary>
멀티스레드 프로그래밍에 대해 설명해보세요.
</summary>
<hr/>

<br/>
<br/>
</details>

<details>
<summary>
Thread-safe 하다는 의미와 설계하는 법을 설명해보세요.
</summary>
<hr/>

<br/>
<br/>
</details>

<details>
<summary>
프로세스 동기화에 대해 설명해보세요.
</summary>
<hr/>

<br/>
<br/>
</details>

<details>
<summary>
교착상태와 기아상태의 해결방법에 대해 설명해보세요.
</summary>
<hr/>

<br/>
<br/>
</details>

<details>
<summary>
세마포어와 뮤텍스의 차이에 대해 설명해보세요.
</summary>
<hr/>

<br/>
<br/>
</details>

<details>
<summary>
가상 메모리에 대해 설명해보세요.
</summary>
<hr/>
  
💬 [가상메모리와 요구 페이징, 페이지 교체](https://flossy-longship-14b.notion.site/Segmentation-3e1d4fe29f324e8e9d451beb58b50dff?pvs=4)

**가상 메모리 시스템(가상기억장치)**

가상 메모리는 프로세스에게 물리적 메모리의 크기를 초과하는 메모리 공간을 제공하는 시스템입니다. 

가상 메모리는 메모리 관리의 효율성을 높이고, 여러 프로그램이 동시에 실행되는 멀티태스킹 환경에서 중요한 역할을 합니다. 가상 메모리는 페이지라는 단위로 나뉘며, 이 페이지들은 필요에 따라 물리적 메모리와 스왑 공간 사이에서 이동합니다. 이 과정을 통해 메모리 사용이 최적화되고, 프로세스 간 격리와 보안이 강화됩니다. 하지만, **스왑 아웃과 스왑 인** 과정에서 발생하는 오버헤드로 인해 성능 저하가 발생할 수도 있습니다. 

✨ Swap 영역은 실제 메모리가 아니기 때문에 지연시간이 많이 발생하며, 가급적이면 Swap 메모리를 사용하지 않도록 설계하는 것이 좋고, 만약 계속해서 사용하는 양이 증가한다면 메모리 누수를 의심해 볼 수 있습니다.

**swap out과 swap in에 대해 더욱 자세히?**

✨ **스왑 아웃과 스왑 인** 과정은 가상 메모리 시스템에서 물리적 메모리의 부족 문제를 해결하기 위해 사용됩니다. 하지만 이 과정에는 **상당한 오버헤드**가 발생합니다. 스왑 아웃은 메모리의 데이터를 디스크로 옮기는 과정이며, 스왑 인은 디스크의 데이터를 다시 메모리로 불러오는 과정입니다. 두 과정 모두 디스크 I/O 작업을 필요로 하며, 이는 상대적으로 느린 작업입니다. 특히, 자주 사용되는 데이터가 스왑 아웃되었다가 스왑 인되는 경우, 시스템의 성능 저하를 초래할 수 있습니다. 따라서, 가상 메모리 시스템을 설계할 때는 이러한 오버헤드를 최소화하는 방향으로 최적화하는 것이 중요합니다

<br/>
<br/>
</details>


<details>
<summary>
캐시의 지역성에 대해 설명해보세요.
</summary>
<hr/>

<br/>
<br/>
</details>

<details>
<summary>프로세스 관련 용어를 설명해보세요. (알아만 둡시다.)
</summary>
<hr/>

<br/>
<br/>
</details>

