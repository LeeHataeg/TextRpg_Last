# TextRpg_Last
---
##구현한 기능 목록

###필수기능

###나만의 아이템(포션)

###인벤토리 크기 맞춤

###상점

###장착 개선

---
##아이템 추가와 아이템 관리
관리의 편의성을 위해 아이템 클래스를 부모클래스로 하여, 각각 무기, 갑옷, 포션을 자식 클래스로 구현했다.
원래는 이를 이용해 아이템 정렬을 아이템 종류 별로 구현하고자 했으나 실력 부족으로 시간이 부족해 구현하지 못했다.

인벤토리는 장비아이템(무기와 갑옷)은 아이템 리스트, 포션아이템은 포션 리스트로 구현하여 구분했다.
상점에서도 장비아이템은 상점 아이템 리스트, 포션아이템은 포션리스트로 구현하여 구분했다.
이는 장비 착용에서 인벤토리 아이템 중 장비아이템, 전투 중 사용 가능 아이템(포션) 등의 특정 아이템만의 호출을 고려했을 때,
포션 등을 분리하는게 이점이 있어 보였다.

인벤토리의 아이템을 어떻게 저장할까 고민했다.
1.스네이크 게임처럼 리스트로 저장
2.아이템 배열로 저장.
  각각의 아이템 객체를 전부 저장하면 메모리 공간을 많이 잡아 먹을 것 같아 전체 갑옷, 무기, 포션을 배열로 묶어두고
  플레이어의 인벤토리나 시작마을의 상점 판매 목록 등은 해당하는 아이템 배열의 인덱스를 정수형 배열로 저장해 필요할 때 호출하려 했으나
  호출하는 시간을 많이 잡아 먹을것 같아 접었다.

해서 그냥 리스트로 저장했다.

---
##아이템 정렬

        string InvenStr_Name = "          |";
        string Replace_Name = string.Empty;
        int nameLength =  myInven[currentItemIndex].Item_Name.Count();
        Replace_Name = InvenStr_Name.Remove(0, nameLength)
                            .Insert(0, myInven[currentItemIndex].Item_Name);

으로 출력될 디폴트 문자열에서 삽입될 텍스트의 글자 수 만큼 앞에서부터 지우고 앞에서부터 붙이는 식으로 진행했다.
추가로 삽입될 정수 타입의 변수가(ex. 가격) 몇자리 정수인지 확인하고자 따로 함수를 작성했다.

        public static int HowManyDigit(int jungsu)
        {
            int i = 0;
            while(true)
            {
                jungsu /= 10;
                if(jungsu <= 0)
                {
                    return (i+1);
                }
            i++;
            }
        }


---
##문자열의 색상을 변경

        Console.ForegroundColor = ConsoleColor.Red;
        Console.Write("문자열");
        Console.ForegroundColor = ConsoleColor.White;

위와 같이 일일이 작성했다.
---
##장착관리

        bool isEquiped = myInven[i].Item_Name.Contains("[E]");
        myInven[exArmorNum].Item_Name = myInven[exArmorNum].Item_Name.Replace("[E]", "");

로 "[E]"라는 특정 문자열이 있는지 확인한 후, 있다면 ""으로 교체해 제거했다.

---
##TIL
<https://blog.naver.com/gkxor031/223189702305>
<https://blog.naver.com/gkxor031/223190655059>
