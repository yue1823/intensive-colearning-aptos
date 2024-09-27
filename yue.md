---
timezone: Asia/Shanghai
---

> 请在上边的 timezone 添加你的当地时区，这会有助于你的打卡状态的自动化更新，如果没有添加，默认为北京时间 UTC+8 时区
> 时区请参考以下列表，请移除 # 以后的内容

timezone: Pacific/Honolulu # 夏威夷-阿留申标准时间 (UTC-10)

timezone: America/Anchorage # 阿拉斯加标准时间 (UTC-9)

timezone: America/Los_Angeles # 太平洋标准时间 (UTC-8)

timezone: America/Denver # 山地标准时间 (UTC-7)

timezone: America/Chicago # 中部标准时间 (UTC-6)

timezone: America/New_York # 东部标准时间 (UTC-5)

timezone: America/Halifax # 大西洋标准时间 (UTC-4)

timezone: America/St_Johns # 纽芬兰标准时间 (UTC-3:30)

timezone: America/Sao_Paulo # 巴西利亚时间 (UTC-3)

timezone: Atlantic/Azores # 亚速尔群岛时间 (UTC-1)

timezone: Europe/London # 格林威治标准时间 (UTC+0)

timezone: Europe/Berlin # 中欧标准时间 (UTC+1)

timezone: Europe/Helsinki # 东欧标准时间 (UTC+2)

timezone: Europe/Moscow # 莫斯科标准时间 (UTC+3)

timezone: Asia/Dubai # 海湾标准时间 (UTC+4)

timezone: Asia/Kolkata # 印度标准时间 (UTC+5:30)

timezone: Asia/Dhaka # 孟加拉国标准时间 (UTC+6)

timezone: Asia/Bangkok # 中南半岛时间 (UTC+7)

timezone: Asia/Shanghai # 中国标准时间 (UTC+8)

timezone: Asia/Tokyo # 日本标准时间 (UTC+9)

timezone: Australia/Sydney # 澳大利亚东部标准时间 (UTC+10)

timezone: Pacific/Auckland # 新西兰标准时间 (UTC+12)

---

# {yue}

1. 自我介绍
  你好，我是一個萌新小白，我也是founder of diffusion ，希望可以讓我的項目更加高的完成度和提升對move語言的了解
2. 你认为你会完成本次残酷学习吗？
那是當然的

# 項目

## 項目名稱：diffusion

## testnet 地址：`0x7776f4ac2f3a13f751b966220b0e68e0b5688682c31e4f93cbf12ce1cea4a7b9`

這個是用來參加黑客松的項目，可以做到下注不同的比賽

Diffusion 是一個基於 Aptos 區塊鏈的 DeFi 聚合器，集成了交換（swap）、去中心化自治組織（DAO）類功能以及下注系統的三合一平台。我們利用 Move 語言和 Move Prover 架構了高度安全的智能合約，並創新推出了更安全的轉帳功能和下注系統，進一步提升了用戶的安全體驗。

Diffusion 結合了多項 Aptos 的特色技術，以及合作夥伴的創新技術，包括無匙帳戶、Nodit、Telegram 機器人和 Mizu Wallet。我們致力於透過這些技術為 Aptos 社區帶來全新的去中心化金融體驗。


## Notes

<!-- Content_START -->

### 2024.09.07

- 学习主题： Aptos & Move 模組學習
- 学习内容总结：
move 到模組學習，從一開始配置aptos cli 和move 的ide環境
```move
module 0x42::HELLOWWORLD{

    use std::debug::print;
    use std::string::utf8;

    #[test]
    fun test_hello_eorld(){
        print(&utf8(b"Hello World")); 
    }
}
````
一開始寫個hellow world 的move 來作為残酷学习的開始，這個可以print hellow world，然後就沒有了XD

### 2024.09.08

今天是學習如何在move裡面print出來，這樣才可以更好的去把bug和error解決

```move
module 0x42::lesson2{
 use std::debug::print;

  struct Wallet has drop{
    balance:u64

  }
    #[test]
    fun test_Wallet(){
        let wallet  = Wallet {balance: 1000};
        let wallet2 = wallet;
        print (&wallet.balance);
        //print (&wallet.balance);

    }

}
```

### 2024.09.09

今天來學習一下move裡面不同的類型， string ， u64，u32，u8 ，vector等等
```move
module 0x42::Type{
    use std::debug::print;
    use std::string;
    use std::string::{utf8};
    #[test_only]
    use std::string::String;

    #[test]
    fun test_num(){
        let num_u8 : u8 = 42; //
        let num_u8_2 =43u8;
        let num_u8_3 :u8 =0x2A; //hash

        let num_u256:u256  = 100_000;
        let num_sum  = (num_u8 as u256) + num_u256 ;

        print(&num_u8);
        print(&num_u8_2);
        print(&num_u8_3);
        print(&num_u256);
        print(&num_sum);
    }

    #[test]
    fun test_bool(){
        let bool_true : bool = true;
        let bool_false : bool =false ;
        print(&bool_true);
        print(&bool_false);
        print(&(bool_true == bool_false));
    }

    #[test]
    fun test_String(){
        let str:String =utf8(b"hellow world");
        print(&str);
    }

    #[test]
    fun test_address(){

        let add:address =@0x2A;
        print(&add);
    }

}
```

### 2024.09.10

今天來寫move 裡面vector的操作
```move
module 0x42::Type{
    use std::debug;
    use std::vector;
    #[test_only]
    use std::bit_vector::is_index_set;

    const APR:vector<u64> = vector[1,2,3,4,5,6,7,8,9,10];
    #[test]
    fun ss(){
        debug::print(&APR)
    }

    #[test]

    fun test_empty_vector(){
        let bools:bool = vector::is_empty(&APR);
        debug::print(&bools);

    }
    #[test]

    fun test_vector_length(){
        let len:u64 =vector::length(&APR);
        debug::print(&len);
    }

    #[test]
    fun test_vector_borrow(){
        let val = vector::borrow(&APR,3);
        debug::print(val)
    }

    #[test]
    fun test_vector_borrow_mut(){
        let arr:vector<u64> = vector[1,2,3,4,5,6,7,8,9,10];
        let val = vector::borrow_mut(&mut arr,3);
        *val=100;
        debug::print(&arr);
    }

    #[test]
    fun test_vector_contain(){
        let n:u64 =3;
        let n2:u64=11;
        let bools:bool = vector::contains(&APR,&n);
        let bools2:bool  = vector::contains(&APR,&n2);
    }

    #[test]
    fun test_vextor_index_of(){
        let n:u64 = 3;
        let n2:u64 = 11;
        let (isIndex,index) = vector::index_of(&APR,&n);
        let (isindex2,index2) = vector::index_of(&APR,&n2);
        debug::print(&isIndex);
        debug::print(&isindex2);
        debug::print(&index);
        debug::print(&index2);


    }

}
```

#### 2024.09.11
```move
module 0x42::Demo{
    use std::debug;
    use std::vector;

    #[test]
    fun test_push_back(){
        let vec = vector[1,2,3];
        vector::push_back(&mut vec ,4);
        debug::print(&vec);

    }

    #[test]
    fun test_append(){
        let vec1= vector[1,2,3];
        let vec2 = vector[4,5,6];
        vector::append(&mut vec1,vec2);
        debug::print(&vec1);

    }

    #[test]
    fun test_rev(){
        let ver1 =vector[1,2,3];
        let ver2 = vector[4,5,6];
        vector::reverse_append(&mut ver1,ver2);
        debug::print(&ver1)

    }
    #[test]
    fun test_pop_back(){
        let vec =vector[1,2,3];
        let x=vector::pop_back(&mut vec);
        debug::print(&x);
        debug::print(&vec);

    }

    #[test]

    fun test_swap(){
        let vec1 = vector[1,2,3,4,5];
        vector::swap(&mut vec1,0,2);
        debug::print(&vec1);
    }
    #[test]
    fun test_reverse(){
        let vec1 = vector[3,5,2,1,4];
        vector::reverse(&mut vec1);
        debug::print(&vec1);


    }


}
```

### 2024.09.12

今天學struct的用法
```move
address 0x42{
    module main{
        use std::debug;
        use std::signer;


        struct Foo has drop{
            u:u64,
            b:bool
        }
        #[test]
        fun oo(){
            let f =Foo{u:42,b:true};
            let Foo{u,b}=f;
            debug::print(&u);
            debug::print(&b);
        }
        #[test]

        fun test2(){
            let f=Foo{u:42,b:true};
            let Foo{ u,b}=&mut f;
            *u=43;
            debug::print(&f.u);
            debug::print(&f.b);

        }

        //copy

        struct Cancopy has copy, drop{
            u:u64,
            b:u64
        }
        #[test]
        fun test3(){
            let f = Cancopy{u:1,b:8};
            let f2 = copy f;
            debug::print(&f2.u);
            debug::print(&f2.b);
            debug::print(&f.u);
            debug::print(&f.b);

        }

        struct Key has key,drop{
            s:Store

        }
        struct Store has store,drop{
            s:u64,y:u64
        }
        #[test]
        fun test4(){
            let y=Store{s:1,y:2};
            let k = Key{s:y};
            debug::print(&k.s.s);
            debug::print(&k.s.y);

        }
    }



}
```

### 2024.09.13

```move
address 0x42{
    module main{
        use std::debug;
        use std::signer;
        #[test]
        fun test_if(){
            let x=6;
            if(x==5){
                debug::print(&x);
            }else{
                debug::print(&10);
            }

        }

        #[test]
        fun test_while(){
            let x= 5;
            while(x>0){
                x=x-1;
                if (x==3){
                    // break;
                    continue;
                };
                debug::print(&x);
            }

        }

        #[test]
        fun test_loop(){
            let x=10;
            loop{
                x=x-1;
                if(x<=5){

                    break
                };
                debug::print(&x);
            };
        return
        }

    }
}
```

### 2024.09.14

friend 的用法

```move
 module MyPacke::main{
        use std::debug;
        friend MyPacke::m2;
        friend MyPacke::m3;
        public fun num():u64{
            66
        }

        public(friend) fun num2():u64{
            88
        }

    }

module MyPacke::m2{

    #[test]
    fun main2(){
        use std::debug;
        use MyPacke::main::num;
        let n=num();
        debug::print(&n);
    }

    #[test]
    fun test2(){
        use std::debug;
        use MyPacke::main::num2;
        let n= num2();
        debug::print(&n);
    }


}

module MyPacke::m3{
    use std::debug;
    #[test]
    fun main3(){
        use std::debug;
        use MyPacke::main::num;
        let n=num();
        debug::print(&n);

    }
    #[test]
    fun test2(){
        use std::debug;
        use MyPacke::main::num2;
        let n= num2();
        debug::print(&n);
    }


}
```
### 2024.09.15

```move
module mynft::mynft{

        use std::string::{String,utf8};
        use std::string;
        use std::option;
        use std::error;

        use std::vector;
        use std::signer;
        use aptos_framework::object::{Self,Object, LinearTransferRef};
        use aptos_token_objects::collection;
        use aptos_token_objects::token;
        use aptos_token_objects::token::Token;
        use aptos_token_objects::property_map;
        use aptos_framework::event;
        use aptos_framework::account;
        use aptos_std::string_utils::{to_string};
        use aptos_std::type_info::struct_name;
        use aptos_framework::fungible_asset::{BurnRef, TransferRef};
        use aptos_token_objects::collection::MutatorRef;
        use aptos_framework::account::SignerCapability;

    #[test_only]
        use aptos_token_objects::aptos_token::create_collection;

        //the token not exist
        const Token_does_not_exist:u64 =1;
        //the provide signer is cretor
        const Not_creator:u64=2;
        const Mycollection:vector<u8> =b"mycollection";
        const Project:address=@0x1;
         struct CollectionRefsStore has key {

             mutator_ref:collection::MutatorRef,

         }
    struct Content has key,drop{
        content:string::String
    }
    #[event]
    struct Mintevent has drop ,store{
        owner:address,
        token_id:address,
        content:string::String
    }
    #[event]
    struct SetContentEvent has drop, store {
        owner: address,
        token_id: address,
        old_content: string::String,
        new_content: string::String
    }
    #[event]
    struct BurnEvent has drop,store {
        owner:address,
        token_id:address,
        content:string::String
    }
    struct Resoucecap has key{
        cap:SignerCapability
    }
    struct Tokenstore has key{
        mutator_ref: token::MutatorRef,
        burn_ref: token::BurnRef,
        extend_ref: object::ExtendRef,
        transfer_ref: option::Option<object::TransferRef>
    }


    fun init_module(caller:&signer){

        let (resource_signer, resource_cap) = account::create_resource_account(
            caller,
            Mycollection
        );

        move_to(&resource_signer,Resoucecap{cap:resource_cap});
        // if (exists<Resoucecap>(signer::address_of(&resource_signer))){
        //     debug::print(&utf8(b"1.yes ResourceCap"));
        // }else{
        //     debug::print(&utf8(b"1.no ResourceCap"));
        // };
        // debug::print(&utf8(Mycollection));

        let max_supply = 1000;
        let des:String = utf8(b"test nft");
        let name:String =utf8(b"nft");
        let web_Addr :String = utf8(b"https://pot-124.4everland.store/IMG_0714.JPG");
        let collection=collection::create_fixed_collection(
            &resource_signer,
            utf8(b"test nft"),
            1000,
            utf8(b"nft"),
            option::none(),
            utf8(b"https://pot-124.4everland.store/IMG_0714.JPG")
        );
        let collection_signer = object::generate_signer(&collection );
        let mutator_ref = aptos_token_objects::collection::generate_mutator_ref(&collection);
        move_to(&collection_signer,CollectionRefsStore{mutator_ref});


        // if (exists<CollectionRefsStore>(signer::address_of(&collection_signer))){
        //     debug::print(&utf8(b"2.yes CollectionRefsStore"));
        // }else{
        //     debug::print(&utf8(b"2.no CollectionRefsStore"));
        // };
    }

    // #[test(caller=@0x1)]
    // fun test_mint(caller:&signer)acquires Resoucecap {
    //     init_module(caller);
    //     let yee : String=utf8(b"1");
    //     mint(caller,yee);
    // }
    //&@mynft
    entry public fun mint(caller :&signer,content:string::String)acquires Resoucecap {
        //let resourf = aptos_framework::account::create_resource_address(&@mynft,Mycollection);

        // debug::print(&utf8(Mycollection));
        // if (exists<Resoucecap>(resourf)){
        //     debug::print(&utf8(b"3.yes Resoucecap"));
        // }else{
        //     debug::print(&utf8(b"3.no Resoucecap"));
        // };

        let resource_cap = &borrow_global<Resoucecap>(aptos_framework::account::create_resource_address(&@mynft,Mycollection)).cap;
        let resource_signer = &account::create_signer_with_capability(resource_cap);
        let token_cref = token::create(resource_signer,utf8(b"nft"),utf8(Mycollection),utf8(b"test nft"),option::none(),utf8(b"https://pot-124.4everland.store/IMG_0714.JPG"));
        let token_signer = object::generate_signer(&token_cref);
        let token_mutator_ref = token::generate_mutator_ref(&token_cref);
        let token_burn_ref =token::generate_burn_ref(&token_cref);
        move_to(
            &token_signer,
            Tokenstore {
                mutator_ref: token_mutator_ref,
                burn_ref: token_burn_ref,
                extend_ref: object::generate_extend_ref(&token_cref),
                transfer_ref: option::none()
            }
        );
        move_to(
            &token_signer,
            Content {
                content
            }
        );


        event::emit(
            Mintevent{
                owner:signer::address_of(caller),
                token_id:object::address_from_constructor_ref(&token_cref),
                content}
        );
        object::transfer(
            resource_signer,
            object::object_from_constructor_ref<Token>(&token_cref),
            signer::address_of(caller),
        );

    }

    entry fun burn(caller:&signer,object:Object<Content>)acquires Tokenstore,Content {
        assert!(object::is_owner(object,signer::address_of(caller)),1);
        let Tokenstore{
            mutator_ref: _,
            burn_ref,
            extend_ref: _,
            transfer_ref: _
        } = move_from<Tokenstore>(object::object_address(&object));

        let Content {
            content
        } = move_from<Content>(object::object_address(&object));
        event::emit(
            BurnEvent {
                owner: object::owner(object),
                token_id: object::object_address(&object),
                content
            }
        );
        token::burn(burn_ref);
    }

    entry fun set_content(
        caller: &signer,
        object: Object<Content>,
        content: string::String
    )acquires Content{
        let old_content =borrow_content(signer::address_of(caller),object).content;
        event::emit(
            SetContentEvent {
                owner: object::owner(object),
                token_id: object::object_address(&object),
                old_content,
                new_content: content
            }
        );
        borrow_mut_content(signer::address_of(caller), object).content = content;
    }
    #[view]
    public fun get_content(object: Object<Content>): string::String acquires Content {
        borrow_global<Content>(object::object_address(&object)).content
    }
    inline fun borrow_content(owner: address, object: Object<Content>): &Content {
        assert!(object::is_owner(object, owner), 1);
        borrow_global<Content>(object::object_address(&object))
    }
    inline fun borrow_mut_content(owner: address, object: Object<Content>): &mut Content {
        assert!(object::is_owner(object, owner), 1);
        borrow_global_mut<Content>(object::object_address(&object))
    }
    #[test_only]
    public fun init_for_test(sender: &signer) {
        init_module(sender)
    }




```

### 2024.09.16

prove 的用法

```move
module 0x1::prove_demo {

    use std::signer;
    use aptos_framework::aptos_coin::AptosCoin;
    use aptos_framework::coin;
    #[test_only]
    use std::string;
    #[test_only]
    use std::string::utf8;
    #[test_only]
    use aptos_std::debug;
    #[test_only]
    use aptos_framework::account::create_account_for_test;
    #[test_only]
    use aptos_framework::system_addresses;
    #[test_only]
    use aptos_framework::timestamp;

    ///Error Code /////
    const To_address_cant_same_with_caller : u64 = 1 ;
    const Amount_must_large_than_zero :u64 = 2 ;
    ///Error Code /////


    spec coin_transfer_to_other( caller:&signer, to_address:address, amount:u64 ) {
        pragma verify = true;

        let addr = signer::address_of(caller);

        ensures  amount > 0 ;
        ensures  addr != to_address;

    }

    public entry fun coin_transfer_to_other (caller:&signer, to_address:address, amount:u64){
        assert!(signer::address_of(caller) != to_address , To_address_cant_same_with_caller);
        assert!(amount >  0 , Amount_must_large_than_zero);

        coin::transfer<AptosCoin>(caller,to_address,amount);

    }

    /////// Unit  Test  /////////

    #[test(aptos_framework=@aptos_framework,caller=@0x2,to_address_signer=@0x3)]
    fun test_coin_transfer(aptos_framework:&signer,caller:&signer,to_address_signer:&signer){
        create_account_for_test(signer::address_of(caller));
        create_account_for_test(signer::address_of(to_address_signer));

        prepare_for_apt(aptos_framework,caller);
        coin::register<AptosCoin>(to_address_signer);

        // 0  transfer
        //coin_transfer_to_other(caller,signer::address_of(to_address_signer),0);

        // self transfer
        //coin_transfer_to_other(caller,signer::address_of(caller),1);

        // transfer 1 APT
        coin_transfer_to_other(caller,signer::address_of(to_address_signer),100000000);

        test_print(caller,to_address_signer);
    }

    #[test_only]
    fun test_print(caller:&signer,to_address:&signer){
        debug::print(&utf8(b"balance of AptosCoin   -  dapp"));
        debug::print(&coin::balance<AptosCoin>(signer::address_of(caller)));
        debug::print(&utf8(b"balance of AptosCoin   -  to address"));
        debug::print(&coin::balance<AptosCoin>(signer::address_of(to_address)));
    }




    #[test_only]
    fun prepare_for_apt(aptos_framework:&signer,caller:&signer){
        timestamp::set_time_has_started_for_testing(aptos_framework);
        let (burn_cap, freeze_cap, mint_cap) = coin::initialize<AptosCoin>(
            aptos_framework,
            string::utf8(b"TC"),
            string::utf8(b"TC"),
            8,
            false,
        );
        coin::register<AptosCoin>(caller);
        let coins = coin::mint<AptosCoin>(200000000, &mint_cap);
        coin::deposit(signer::address_of(caller), coins);
        coin::destroy_freeze_cap(freeze_cap);
        coin::destroy_burn_cap(burn_cap);
        system_addresses::assert_aptos_framework(aptos_framework);
        coin::destroy_mint_cap(mint_cap);
    }
}

```

### 2024.09.17

寫一個test 的用法

```move
module 0x1::test {

    use std::signer;
    use std::string::utf8;
    use aptos_framework::coin;
    use aptos_framework::coin::{destroy_burn_cap, destroy_freeze_cap, register, destroy_mint_cap};
    #[test_only]
    use aptos_std::debug;
    #[test_only]
    use aptos_framework::account::create_account_for_test;

    //// Const /////

    const Coin_name : vector<u8> = b"diffusion";
    const Coin_symbol :vector<u8> = b"dfc";
    const Coin_decimals :u8 = 8;

    //// Const /////

    struct Diffusion_coin has key {}

    fun init_module (caller:&signer){
        let (burn,freeze,mint) = coin::initialize<Diffusion_coin>(caller,utf8(Coin_name),utf8(Coin_symbol),Coin_decimals,false);
        destroy_burn_cap(burn);
        destroy_freeze_cap(freeze);
        let coins = coin::mint<Diffusion_coin>(1000,&mint);
        register<Diffusion_coin>(caller);
        coin::deposit(signer::address_of(caller),coins);
        destroy_mint_cap(mint);
    }
    public entry fun coin_transfer_to_other(caller:&signer,to_address:address){
        coin::transfer<Diffusion_coin>(caller,to_address,100);
    }


    /////// Unit Test  /////////

    // #[test(caller=@0x1,to_address=@0x2)]
    //  fun test_coin_transfer_to_other(caller:&signer,to_address:&signer){
    //     create_account_for_test(signer::address_of(caller));
    //     create_account_for_test(signer::address_of(to_address));
    //     init_module(caller);
    //     register<Diffusion_coin>(to_address);
    //     //test_print(caller,to_address);
    //     coin_transfer_to_other(caller,signer::address_of(to_address));
    //      test_print(caller,to_address);
    //  }

    #[test_only]
    fun test_print(caller:&signer,to_address:&signer){
        debug::print(&utf8(b"balance of diffusion coin   -  dapp"));
        debug::print(&coin::balance<Diffusion_coin>(signer::address_of(caller)));
        debug::print(&utf8(b"balance of diffusion coin   -  to address"));
        debug::print(&coin::balance<Diffusion_coin>(signer::address_of(to_address)));
    }


}

```

```move
module 0x1::demo {
    use std::signer;
    use std::string;
    use std::string::utf8;
    use aptos_std::debug;

    struct Profile has key{
        name:string::String,
        icon:string::String
    }

    fun init_module(caller:&signer){
        let new_Profile = Profile{
            name:utf8(b"hello"),
            icon:utf8(b"is me")
        };
        move_to(caller,new_Profile);
    }

    public entry fun read_profile (caller:&signer) acquires Profile {
        let borrow_name = borrow_global<Profile>(signer::address_of(caller)).name;
        let borrow_icon = borrow_global<Profile>(signer::address_of(caller)).icon;
        debug::print(&utf8(b"name"));
        debug::print(&borrow_name);
        debug::print(&utf8(b"icon"));
        debug::print(&borrow_icon);
    }


    /////// Unit Test  /////////

    // #[test(caller=@0x1)]
    // fun test_read_profile(caller:&signer) acquires Profile {
    //     //init_module(caller);
    //     read_profile(caller);
    // }

}

```

### 2024.09.18

寫個hackthon 要用到的move 函數，先寫view
```move
    ////////////////// view fun /////////////////////////////////
    #[view]
    public fun check_user_card(user_address:address,card_name:string::String,expired_date:u64):(bool,Bet_card) acquires Account_tree {
        let have_or_not = false;
        let i =0;
        let index =99;
        let length = vector::length(&borrow_global<Account_tree>(user_address).save_2);
        while(i < length){
            let borrow = vector::borrow(&borrow_global<Account_tree>(user_address).save_2,i);
            if(borrow.expired_time == expired_date){
                if(borrow.pair.pair_name == card_name){
                    index =i;
                    have_or_not=true;
                }
            };
            i = i +1;
        };
        let null_bet = Bet_card{
            account:@0x1,
            which:99,
            pair:Pair{
                pair_type:utf8(b""),
                pair_name:utf8(b""),
                left_url:utf8(b""),
                right_url:utf8(b""),
                left:0,
                left2:0,
                middle:0,
                middle2:0,
                right:0,
                right2:0,
                can_bet:false,
                expired_time:0
            },
            bet:0,
            a_win:0,
            b_win:0,
            c_win:0,
            time:0,
            expired_time:0,
        };
        if(i != 99 ){
            return (have_or_not,*vector::borrow(&borrow_global<Account_tree>(user_address).save_2,i))
        }else{return (have_or_not,null_bet)}
    }
    #[view]
    public fun check_user_badges(user_address:address,badges_name:string::String):(bool,Badges,vector<Badges>) acquires Diffusion_store_tree, Account_tree {
        let borrow = borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list;
        let i=0;
        let length = vector::length(&borrow);
        let right = false;
        let index = 99;
        while(i < length) {
            let specfic = vector::borrow(&borrow, i);
            if (specfic.save_Badges.Name == badges_name) {
                let f = 0;
                let length2 = vector::length(&specfic.save_list);
                index = i;
                while (f < length2) {
                    let specfic_address = vector::borrow(&specfic.save_list, f);
                    if (specfic_address == &user_address) {
                        right = true;
                    };
                    f = f + 1;
                };
            };
            i = i + 1;
        };
        if(index != 99){return (right,  vector::borrow(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_Badges,borrow_global<Account_tree>(user_address).save_4)}else{
            let new_badges = Badges{ Name:utf8(b""),url:utf8(b"")};
            return(false , new_badges,vector::empty<Badges>())
        }

    }
    #[view]
    public fun check_helper_list(helper_address:address):(bool,bool) acquires Diffusion_store_tree {
        let borrow = borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list;
        let i=0;
        let length = vector::length(&borrow);
        let right1=false;
        let right2 = false;
        while(i < length){
            let specfic_helper = vector::borrow(&borrow,i);
            if(specfic_helper.account == helper_address){
                right1=true;
                if(specfic_helper.pay_margin == true){
                    right2=true
                };
            };

            i=i+1;
        };
        return (right1,right2)
    }
    #[view]
    public fun helper_upload_which_result(helper_address:address):Helper  acquires Diffusion_store_tree {

        let i=0;
        let length = vector::length(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list);
        let index= 99;
        while(i < length){
            let specfic_helper = vector::borrow(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list,i);
            if(specfic_helper.account == helper_address){
                index = i ;
            };
            i=i+1;
        };
        if(index !=99){*vector::borrow(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list,index)}else{
            let new_helper = Helper{
                account:@0x1,
                helper_contribute:vector::empty<Helper_upload_result>(),
                helper_point:0,
                upload_times:0,
                wrong_times:0,
                pay_margin:false,
                need_admin:false,
            };
            return new_helper
        }

    }
    #[view]
    public fun get_pair_data(pair_name:string::String,expire_data:u64):(Pair,Chips,bool,bool) acquires Diffusion_store_tree {
        let borrow = borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Pair_result_store.save_pair;
        let i = 0 ;
        let length = vector::length(&borrow);
        let index= 99;
        while(i < length ){
            let specfic_pair = vector::borrow(&borrow,i);
            if(specfic_pair.pair_name == pair_name){
                    if(specfic_pair.expired_time == expire_data){
                        index =i
                    };
                };
            i=i+1;
        };
        if(index !=99){
            return (*vector::borrow(&borrow,index),*vector::borrow(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Pair_result_store.save_chips,index),*vector::borrow( &borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Pair_result_store.save_admin_set_result,index),*vector::borrow( &borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Pair_result_store.save_can_claim,index))}
        else{
            let new_pair = Pair{
                pair_type:utf8(b""),
                pair_name:utf8(b""),
                left:0,
                left2:0,
                middle:0,
                middle2:0,
                right:0,
                right2:0,
                left_url:utf8(b""),
                right_url:utf8(b""),
                expired_time:0,
                can_bet:false
            };
            let new_chips = Chips{
                left:0,
                middle:0,
                right:0,
                given:0
            };
            return (new_pair,new_chips,false,false)
        }

    }
```

### 2024.09.19

```move  ////////////////// Helper fun /////////////////////////////////
    public entry fun helper_upload_result(caller:&signer,pair_name1:string::String,which:u8,expired_time:u64) acquires Diffusion_store_tree, Account_tree {
        // if(vector::length(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list) >= (Least_helper as u64)){
        //     all_helper_result(caller);
        // };
        // all_helper_result(caller);
        assert!(exists<Account_tree>(signer::address_of(caller)  )== true,Create_account_first);
        assert!(exists<Diffusion_store_tree>(create_resource_address(&@dapp,Seed))== true,Not_exists_diffusion_store_tree);

        too_much_wrong_is_time_to_click_it_out(caller);
        asc3(caller);

        let helper_index = check_helper_index(caller);
        assert!(helper_index !=99,NOT_HELPER);
        assert!(which==1||which==2||which==3,NOT_RIGHT_INPUT);


        let pair_index = check_pair_index(caller,pair_name1,expired_time);
        assert!(pair_index!=99,NOT_exist_pair);
        assert!(vector::borrow(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Pair_result_store.save_pair,pair_index).can_bet == false , Still_Bet_time);
        let helper_upload_result_index  = check_helper_upload_result_index(caller,pair_index,helper_index);

        assert!(helper_upload_result_index==99,ALREADY_UPLOAD);

        let admin_set =vector::borrow(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Pair_result_store.save_admin_set_result,pair_index) ;
        let can_claim = vector::borrow(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Pair_result_store.save_can_claim,pair_index) ;

        assert!(admin_set != &true && can_claim!=&true,Pair_finish);

        let borrow_helper_list = borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed));
        let specfic_helper = vector::borrow_mut(&mut borrow_helper_list.save_Helper_list.list,helper_index);

        assert!(specfic_helper.pay_margin==true,Helper_not_pay_margin);

       // let borrow_pair_reult = borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Pair_result_store;
        let spedcfic_pair = vector::borrow(&borrow_helper_list.save_Pair_result_store.save_pair,pair_index);

        let new_upload_result = Helper_upload_result{
            pair:Pair{
                pair_type:spedcfic_pair.pair_type,
                pair_name:spedcfic_pair.pair_name,
                left_url:spedcfic_pair.left_url,
                right_url:spedcfic_pair.right_url,
                left:spedcfic_pair.left,
                left2:spedcfic_pair.left2,
                middle:spedcfic_pair.middle,
                middle2:spedcfic_pair.middle2,
                right:spedcfic_pair.right,
                right2:spedcfic_pair.right2,
                can_bet:spedcfic_pair.can_bet,
                expired_time:spedcfic_pair.expired_time
            },
            result:which,
            upload_time:timestamp::now_seconds(),
            right_or_not:vector::empty<bool>()
        };


        vector::push_back(&mut specfic_helper.helper_contribute,new_upload_result);
        // debug::print(&utf8(b"upload result"));
        // debug::print(&specfic_helper.helper_contribute);
        specfic_helper.upload_times = specfic_helper.upload_times + 1;

    }

    public entry fun apply_to_be_helper(caller:&signer) acquires Diffusion_store_tree, Account_tree {
        let helper_index = check_helper_index(caller);
        assert!(helper_index!=99,NOT_HELPER);
        assert!(exists<Account_tree>(signer::address_of(caller)),Create_account_first);

        // let helper_vector = borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed));
        // let specfic_helper = vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list,helper_index);
         if(vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list,helper_index).pay_margin == false){
            pay_margin_to_account(caller);
            vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list,helper_index).pay_margin=true;
            let helper_badges = Badges{Name:utf8(b"Helper"),url:utf8(b"https://pot-124.4everland.store/helper_badges.png")};
            vector::push_back(&mut borrow_global_mut<Account_tree>(signer::address_of(caller)).save_4,helper_badges);
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_helper_chance.heler_number = borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_helper_chance.heler_number+1;
        }else{
            assert!(vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list,helper_index).pay_margin != true,Already_pay_margin);
        }


    }


    public entry fun mint_badges(caller:&signer,badges:string::String) acquires Diffusion_store_tree, Account_tree {
        let i= 0;
        let length =vector::length(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list);
        let index =99;
        while(i < length ){
            let specfic = vector::borrow(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,i);
            if(specfic.save_Badges.Name ==badges){
                index = i;
            };
            i=i+1;
        };
        assert!(index != 99 ,Dont_have_this_badges);
        if (vector::borrow(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_can_mint == true){
            let e = 0 ;
            let length3 = vector::length(&vector::borrow(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_allow_list);
            while(e < length3 ) {
                let specfi_borrow = vector::borrow(
                    &vector::borrow(
                        &borrow_global_mut<Diffusion_store_tree>(
                            create_resource_address(&@dapp, Seed)
                        ).save_badges_list,
                        index
                    ).save_allow_list,
                    e
                );
                if (specfi_borrow == &signer::address_of(caller)) {
                    let f = 0 ;
                    let length2 = vector::length(&borrow_global<Account_tree>(signer::address_of(caller)).save_4);
                    let where = 99;
                    while(f < length2){
                        let specfic = vector::borrow(&borrow_global<Account_tree>(signer::address_of(caller)).save_4,f);
                        if(specfic.Name == badges){
                            where = f;
                        };
                        f=f +1;
                    };
                    assert!(where == 99 ,Already_exists_this_badges);
                    let new_badges = Badges{
                        Name:vector::borrow(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_Badges.Name,
                        url:vector::borrow(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_Badges.url,
                    };
                    push_back(&mut borrow_global_mut<Account_tree>(signer::address_of(caller)).save_4,new_badges);
                    vector::push_back(&mut vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_list , signer::address_of(caller));
                };
                e = e + 1;
            }
        }else{
            let f = 0 ;
            let length2 = vector::length(&borrow_global<Account_tree>(signer::address_of(caller)).save_4);
            let where = 99;
            while(f < length2){
                let specfic = vector::borrow(&borrow_global<Account_tree>(signer::address_of(caller)).save_4,f);
                if(specfic.Name == badges){
                    where = f;
                };
                f=f +1;
            };
            assert!(where == 99 ,Already_exists_this_badges);
            let new_badges = Badges{
                Name:vector::borrow(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_Badges.Name,
                url:vector::borrow(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_Badges.url,
            };
            push_back(&mut borrow_global_mut<Account_tree>(signer::address_of(caller)).save_4,new_badges);
            vector::push_back(&mut vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_list , signer::address_of(caller));
        }
    }
    ////////////////// Helper fun /////////////////////////////////

```

寫一下helper會用到的function

### 2024.09.20
```move
////////////////// Admin fun /////////////////////////////////

    public entry fun admin_set_badges(caller:&signer,job:string::String,badges:string::String,target:address,set_can_mint:bool) acquires Diffusion_store_tree {
        let admin_index = check_admin_index(signer::address_of(caller));
        assert!(admin_index !=99 ||signer::address_of(caller)==@admin1 || signer::address_of(caller)==@admin1,Not_admin);
        let i= 0;
        let length =vector::length(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list);
        let index =99;
        while(i < length ){
            let specfic = vector::borrow(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,i);
            if(specfic.save_Badges.Name ==badges){
                index = i;
            };
            i=i+1;
        };
        assert!(index != 99 ,Dont_have_this_badges);
        if(job == utf8(b"add")){
            vector::push_back(&mut vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_allow_list,target);
        }
        else if(job == utf8(b"minus")){
            let f =0;
            let length2 = vector::length(&vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_allow_list);
            let where =99;
            while(f < length2 ){
                let borrow = vector::borrow(&vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_allow_list,f);
                if(borrow == &target){
                    where = f;
                };
                f= f+1;
            };
            assert!(f != 99 ,Dont_have_this_address_in_allow_list);
            vector::remove(&mut vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_allow_list,where);
        }
        else if(job == utf8(b"set")){
            vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,index).save_can_mint = set_can_mint;
        }

    }
    fun check_admin_index(target:address):u64 acquires Diffusion_store_tree {
        let i = 0;
        let length =vector::length(& borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.admin_list);
        while(i < length){
            let borrow = vector::borrow(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.admin_list,i);
            if(&target == borrow){
                return i
            };
            i=i+1;
        } ;
        return 99
    }
    public entry fun admin_set_admin (caller:&signer,add_or_delete:string::String,target_address:address) acquires Diffusion_store_tree {
        assert!(signer::address_of(caller)==@admin1 || signer::address_of(caller)==@admin1,Not_lages_admin);
        assert!(exists<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)) == true,Not_exists_diffusion_store_tree);
        let admin_index = check_admin_index(target_address);

        if(add_or_delete == utf8(b"add")){
            assert!(admin_index ==99 ,Already_have_this_admin);
            vector::push_back(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.admin_list,target_address);
        }else if(add_or_delete == utf8(b"delete")){
            assert!(admin_index !=99,Dont_have_this_admin );
            vector::remove(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.admin_list,admin_index);
        }
    }
    public entry fun admin_said_times_up(caller:&signer,pair:string::String,expired_time:u64) acquires Diffusion_store_tree {
        let admin_index = check_admin_index(signer::address_of(caller));
        assert!(admin_index !=99 || signer::address_of(caller)==@admin1 || signer::address_of(caller)==@admin1,Not_admin);
        let index = check_pair_index(caller,pair,expired_time);
        assert!(index != 99 ,NOT_exist_pair);
        vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Pair_result_store.save_pair,index).can_bet = false ;
    }
    public entry fun create_or_delete_badges (caller:&signer,create_or_delete:string::String,badges:string::String,url1:string::String,can_mint:bool) acquires Diffusion_store_tree {
        assert!(signer::address_of(caller)==@admin1 || signer::address_of(caller)==@admin1,Not_admin);
        let i= 0;
        let length =vector::length(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list);
        let index =99;
        while(i < length ){
            let specfic = vector::borrow(&borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,i);
            if(specfic.save_Badges.Name ==badges){
                index = i;
            };
            i=i+1;
        };

        if(create_or_delete == utf8(b"create")){
            assert!(index == 99 ,Already_exists_this_badges);
            let new_badges=Badges_list{
                save_Badges:Badges{Name:badges,url:url1},
                save_can_mint:can_mint,
                save_allow_list:vector::empty(),
                save_list:vector::empty(),
            };
            push_back(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_badges_list,new_badges);
        }
        else if(create_or_delete == utf8(b"delete")){
            if(length != 0) {
                assert!(index != 99, Dont_have_this_badges);
                vector::remove<Badges_list>(
                    &mut borrow_global_mut<Diffusion_store_tree>(
                        create_resource_address(&@dapp, Seed)
                    ).save_badges_list,
                    index
                );
            }
        }
    }
    public entry fun set_chance(caller:&signer,which_one:string::String,fee1:u64,fee2:u64) acquires Diffusion_store_tree {
        assert!(signer::address_of(caller)==@admin1 || signer::address_of(caller)==@admin2 ,Not_admin);
        assert!(exists<Diffusion_store_tree>(create_resource_address(&@dapp,Seed))==true,Not_exists_diffusion_store_tree);
        if(which_one==utf8(b"margin")){
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).fee.margin=fee1;
        }else if(which_one==utf8(b"fee")){
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).fee.fees_1=fee1;
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).fee.fees_2=fee2;
        }else if(which_one==utf8(b"share")){
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).fee.allocation_share_1=fee1;
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).fee.allocation_share_2=fee2;
        }else if(which_one==utf8(b"max helper")){
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_helper_chance.maximun_helper_num=fee1;
        }else if(which_one==utf8(b"least helper")){
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_helper_chance.least_helper_result= (fee1 as u8);
        }else if(which_one==utf8(b"wrong")){
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_helper_chance.chance_for_wrong_time= (fee1 as u8);

        }else if(which_one==utf8(b"nft chance")){
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).fee.nft_chance_1 = fee1 ;
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).fee.nft_chance_2 = fee2 ;
        }else if(which_one==utf8(b"bank share")){
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).fee.bank_share_1 = fee1 ;
            borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).fee.bank_share_2 = fee2 ;
        };
    }
    public entry fun set_cylinder_sav_number(caller:&signer,save_number:u64,coin1:string::String,coin_address1:address,send_coin_amount1:u64) acquires Diffusion_store_tree {
        assert!(signer::address_of(caller) == @admin1 ||signer::address_of(caller) == @admin2 ,Not_admin  );
        assert!(save_number > 1 ,Save_number_must_large_than_1 );
        let index = find_coin_index_in_main_tree(coin1,coin_address1,send_coin_amount1);
        assert!(index != 99 ,Dont_have_this_cylinder);
        vector::borrow_mut(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Cylinder_Pairs,index).save_number = save_number;
    }
    public entry fun create_cylinder(caller:&signer,coin1:string::String,coin_address1:address,send_coin_amount1:u64) acquires Diffusion_store_tree {
        let admin_index = check_admin_index(signer::address_of(caller));
        assert!(admin_index != 99 ||signer::address_of(caller) == @admin1 ||signer::address_of(caller) == @admin2 ,Not_admin  );
        let index = find_coin_index_in_main_tree(coin1,coin_address1,send_coin_amount1);
        assert!(index == 99 ,Already_have_this_cylinder);
        let new_cylinder = Cylinder_Pairs{
            coin:coin1,
            coin_address:coin_address1,
            pair_number:send_coin_amount1,
            save_number:1,
            save_total:0,
            send_amount_vector:vector::empty<u64>(),
            send_address_vector:vector::empty<address>(),
            already_send:0
        };
        // vector::push_back(&mut new_cylinder.send_address_vector,@admin1);
        // vector::push_back(&mut new_cylinder.send_amount_vector,1);
        vector::push_back(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Cylinder_Pairs,new_cylinder);
    }
    public entry fun create_helper(caller:&signer,add_or_delete:string::String,helper_adddress:address) acquires Diffusion_store_tree {
        assert!(signer::address_of(caller)==@admin1 || signer::address_of(caller)==@admin2 ,Not_admin);
        if(add_or_delete == utf8(b"add")) {
            assert!(
                (vector::length(
                    &borrow_global_mut<Diffusion_store_tree>(
                        create_resource_address(&@dapp, Seed)
                    ).save_Helper_list.list
                ) < borrow_global_mut<Diffusion_store_tree>(
                    create_resource_address(&@dapp, Seed)
                ).save_helper_chance.maximun_helper_num),
                Too_Much_Helper
            );
            let borrow_helper_list = borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp, Seed));
            let length = vector::length(&borrow_helper_list.save_Helper_list.list);
            let i = 0;
            let done = false;
            if (length == 0) {
                let new_helper = Helper {
                    account: helper_adddress,
                    helper_contribute: vector::empty<Helper_upload_result>(),
                    helper_point: 0,
                    upload_times: 0,
                    wrong_times: 0,
                    pay_margin: false,
                    need_admin: false
                };
                vector::push_back(&mut borrow_helper_list.save_Helper_list.list, new_helper);
            }else {
                while (i < length) {
                    let borrow = vector::borrow(&borrow_helper_list.save_Helper_list.list, i);
                    if (borrow.account == helper_adddress) {
                        return
                    };
                    if (i == length - 1) {
                        done = true
                    };
                    i = i + 1;
                };

                if (done == true) {
                    let new_helper = Helper {
                        account: helper_adddress,
                        helper_contribute: vector::empty<Helper_upload_result>(),
                        helper_point: 0,
                        upload_times: 0,
                        wrong_times: 0,
                        pay_margin: false,
                        need_admin: false
                    };
                    vector::push_back(&mut borrow_helper_list.save_Helper_list.list, new_helper);
                };
            };
        }else if(add_or_delete == utf8(b"delete")){
            let i =0;
            let length = vector::length(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list);
            let index= 99;
            while(i < length){
                let specfic = vector::borrow(&borrow_global<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list,i);
                if(specfic.account ==helper_adddress){
                    index = i;
                };
                i=i+1;
            };
            assert!(index != 99 , Dont_have_this_helper);
            vector::remove(&mut borrow_global_mut<Diffusion_store_tree>(create_resource_address(&@dapp,Seed)).save_Helper_list.list,index);
        }
        // let helper_index = check_helper_index(caller);
        // assert!(helper_index!=99,NOT_HELPER);
    }

    ////////////////// Admin fun /////////////////////////////////
```
寫admin會用到的function

### 2024.09.21

今天來學習 object 的用法和理解
`https://www.youtube.com/watch?v=bny8hBEpBmw`

### 2024.09.22

```move
module dapp::aptos_discover {

    use std::option;
    use std::signer;
    use std::signer::address_of;
    use std::string;
    use std::string::utf8;
    use aptos_std::smart_vector;
    use aptos_framework::account;
    use aptos_framework::account::{SignerCapability, create_resource_address, create_signer_with_capability};
    use aptos_framework::object;
    use aptos_framework::object::{disable_ungated_transfer, DeleteRef};
    use aptos_framework::primary_fungible_store::create_primary_store_enabled_fungible_asset;
    use aptos_framework::resource_account::create_resource_account;
    use aptos_framework::fungible_asset;
    #[test_only]
    use std::vector;
    #[test_only]
    use aptos_std::debug;
    #[test_only]
    use aptos_framework::object::ObjectCore;

    const Seed:vector<u8> = b"discover";

    //Error  code
    const No_q_set:u64=1;
    const Not_exist_problem_set :u64 = 2;
    const No_this_image :u64 = 3;

    struct Resource_store_object has key {
        object:address
    }
    struct ChainMark_Object_cap has key , store {
        trans_cap : object::TransferRef,
        exten_cap : object::ExtendRef
    }
    struct ChainMark_FA_cap has key,store{
        mint_cap:fungible_asset::MintRef,
        burn_cap : fungible_asset::BurnRef,
        trans_cap  : fungible_asset::TransferRef
    }

    struct Object_cap has key , store {
        trans_cap : object::TransferRef,
        del_cap : object::DeleteRef,
       exten_cap : object::ExtendRef
    }


    struct ResourceCap has key{
        cap:SignerCapability
    }
    //owner of organiztion
    struct Organization has key,store{
        name:string::String,
        address:address,
        organization_discribe:string::String
    }
    //problem want to soleve
    struct Problem has key ,store{
        problem:string::String,
        owner_address:address,
        date:string::String
    }

    //data which want to aptos community to mark
    struct Q_set has key,store {
        img_url_set : smart_vector::SmartVector<string::String>,
        true_number:u64,
        false_number:u64,
        answer_number:u64,
        reward:u64,
    }
    // user answer data
    struct User_answer has key,store{
        image:string::String,
        index_of_smart_vector:u64,
        answer:bool,
        user_address:address,
        date:string::String,
    }
    /// store all data
    struct Problem_set has key {
        owner:Organization,
        problem_details:Problem,
        question:Q_set,
        true_answer:smart_vector::SmartVector<User_answer>,
        false_answer:smart_vector::SmartVector<User_answer>
    }

    // for Organization

    public entry fun create_problem_set (caller:&signer,problem1:string::String,date1:string::String,descibe:string::String,name_of_Organization:string::String,image_vector:vector<string::String>,reward_budget:u64) acquires  ResourceCap {
        let new_organ = Organization{
            name:name_of_Organization,
            address:address_of(caller),
            organization_discribe:descibe
        };
        let new_smart_vector =smart_vector::empty<string::String>();
        smart_vector::add_all(&mut new_smart_vector,image_vector);
        let new_q_set = Q_set{
            img_url_set:new_smart_vector,
            true_number:0,
            false_number:0,
            answer_number:0,
            reward:reward_budget
        };
        let new_Problem = Problem{
            problem:problem1,
            owner_address:address_of(caller),
            date:date1
        };

        let resource =&borrow_global<ResourceCap>(create_resource_address(&@dapp,Seed)).cap;
        let resouces_signer = &create_signer_with_capability(resource);

        let new_object = &object::create_object(address_of(resouces_signer));
        let object_signer = &object::generate_signer(new_object);

        let new_del_red = object::generate_delete_ref(new_object);
        let new_trans_ref = object::generate_transfer_ref(new_object);
        let new_extent_ref = object::generate_extend_ref(new_object);

        let new_problem_set = Problem_set{
            owner:new_organ,
            problem_details:new_Problem,
            question:new_q_set,
            true_answer:smart_vector::empty<User_answer>(),
            false_answer:smart_vector::empty<User_answer>()
        };
        move_to(caller,Object_cap{
            trans_cap:new_trans_ref,
            del_cap:new_del_red,
            exten_cap:new_extent_ref,
        });

        move_to(resouces_signer,Resource_store_object{object:address_of(object_signer)});
        move_to(object_signer,new_problem_set);
    }

    // for user

    public entry fun answer_question(caller:&signer,image_url:string::String,answer1:bool,data1:string::String,problem_set_address:address) acquires Problem_set, ResourceCap {
        let resource = &borrow_global<ResourceCap>(create_resource_address(&@dapp,Seed)).cap;
        let resource_signer = &create_signer_with_capability(resource);
        assert!(exists<Problem_set>(problem_set_address),Not_exist_problem_set);
        let index = find_index(problem_set_address,image_url);
        let borrow = borrow_global_mut<Problem_set>(problem_set_address);
        assert!(index != 9999999,No_this_image);
        let conf = object::create_object(address_of(resource_signer));
        let new_user_anser = User_answer{
            image:image_url,
            index_of_smart_vector:index,
            answer:answer1,
            user_address:address_of(caller),
            date:data1
        };
        if (answer1){
            smart_vector::push_back(&mut borrow.true_answer,new_user_anser);
            borrow.question.true_number=borrow.question.true_number+1;
            borrow.question.answer_number= borrow.question.answer_number+1;
        }else{
            smart_vector::push_back(&mut borrow.false_answer,new_user_anser);
            borrow.question.false_number=  borrow.question.false_number+1;
            borrow.question.answer_number= borrow.question.answer_number+1;
        }
    }

    //logic

    fun find_index (caller:address,image_target:string::String):u64 acquires Problem_set {
        let length = smart_vector::length(&borrow_global<Problem_set>(caller).question.img_url_set);
        let index = 9999999;
        let  i= 0;
        while (i < length ){
            let borrow_target = smart_vector::borrow(&borrow_global<Problem_set>(caller).question.img_url_set,i);
            if(&image_target == borrow_target){
                index = i;
            };
            i = i+1;
        };
        return index
    }

    fun init_module(caller:&signer) {
        let (resource_signer, resource_cap) = account::create_resource_account(
                    caller,
                Seed
                );
        move_to(&resource_signer,ResourceCap{cap:resource_cap});
        let new_object_cons = object::create_named_object(&resource_signer,Seed);
        let new_trans_ref = object::generate_transfer_ref(&new_object_cons);
        let new_extent_ref = object::generate_extend_ref(&new_object_cons);

        disable_ungated_transfer( &new_trans_ref);
        let object_signer = &object::generate_signer(&new_object_cons);
         create_primary_store_enabled_fungible_asset(
             &new_object_cons,
         option::none(),
             utf8(b"ChainMark Coin"),
             utf8(b"CMC"),
             8,
             utf8(b"https://raw.githubusercontent.com/dylan12386/aptos_discover/refs/heads/main/ChainMARK.jpeg"),
             utf8(b"https://github.com/dylan12386/aptos_discover")
         );
        let mint_ref = fungible_asset::generate_mint_ref(&new_object_cons);
        let burn_ref = fungible_asset::generate_burn_ref(&new_object_cons);
        let tran_ref = fungible_asset::generate_transfer_ref(&new_object_cons);
        move_to(&resource_signer,ChainMark_FA_cap{
            mint_cap:mint_ref,
            burn_cap:burn_ref,
            trans_cap:tran_ref
        });
        move_to(&resource_signer,ChainMark_Object_cap{
            trans_cap:new_trans_ref,
            exten_cap:new_extent_ref,
        })
    }


    // test
    #[test(caller=@dapp,organisztion_signer=@0x4)]
    fun test_init (caller:&signer,organisztion_signer:&signer) acquires ResourceCap, ChainMark_Object_cap {
        init_module(caller);
        let image_vector =vector::empty<string::String>();
        vector::push_back(&mut image_vector,utf8(b"aaa"));
        vector::push_back(&mut image_vector,utf8(b"bbb"));
        create_problem_set(organisztion_signer,utf8(b"solve image of A"),utf8(b"2024/09/22 - 2024/12/15"),utf8(b"help us mark  down the image isn't A , we will use it to tran AI "),utf8(b"Test Company"),image_vector,100000000);

        borrow_global<Problem_set>()

        answer_question();
        let object_extend = &borrow_global<ChainMark_Object_cap>(create_resource_address(&@dapp,Seed)).exten_cap;
        let object_signer = &object::generate_signer_for_extending(object_extend);
        debug::print(&object::address_to_object<ObjectCore>(address_of(object_signer)));
    }
}

```
寫一個object的用法，但是沒有寫完

### 2024.09.23

`https://aptos.dev/en/build/create-aptos-dapp`

使用create aptos dapp 去做一個新的模板，可以直接改去用

### 2024.09.24

```move
fun increase_CHP (caller:&signer,user1:address) acquires ChainMark_FA_cap {

        let obj_address = object::create_object_address(&create_resource_address(&@dapp,Seed),Seed);
        let meta_data = object::address_to_object<Metadata>(obj_address);
        let borrow = borrow_global<ChainMark_FA_cap>(obj_address);
        // let obj_address = borrow_global<Resource_store_object>(create_resource_address(&@dapp,Seed)).object;
        // let new_coin=fungible_asset::mint(&borrow.mint_cap,100000000);
         primary_fungible_store::mint(&borrow.mint_cap,signer::address_of(caller),100000000);

        primary_fungible_store::mint(&borrow.mint_cap,user1,100000000);

         debug::print(&utf8(b"caller CHC Balance"));
         debug::print(& primary_fungible_store::balance(signer::address_of(caller),meta_data));

        debug::print(&utf8(b"user CHC Balance"));
        debug::print(& primary_fungible_store::balance(user1,meta_data));

        // let new_object = object::address_to_object<>(obj_address);
        //fungible_asset::deposit(caller);
        //primary_fungible_store::deposit(signer::address_of(caller),new_coin);

    }

```
更進一步去了解onbject 要怎麼做一個v2 的代幣

### 2024.09.25

```move
// test
    #[test(caller=@dapp,organisztion_signer=@0x4,user1=@0x789)]
    fun test_init (caller:&signer,organisztion_signer:&signer,user1:&signer) acquires ResourceCap, Problem_set, Resource_store_object, ChainMark_FA_cap, Object_cap {
        init_module(caller);
        let image_vector =vector::empty<string::String>();
        vector::push_back(&mut image_vector,utf8(b"aaa"));
        vector::push_back(&mut image_vector,utf8(b"bbb"));
        create_problem_set(organisztion_signer,utf8(b"solve image of A"),utf8(b"2024/09/22 - 2024/12/15"),utf8(b"help us mark  down the image isn't A , we will use it to tran AI "),utf8(b"Test Company"),image_vector,100000000);
        let address1 = borrow_global<Resource_store_object>(create_resource_address(&@dapp,Seed)).object;
        answer_question(user1,utf8(b"aaa"),true,utf8(b"2024/09/22"),address1);
        // let object_extend = &borrow_global<ChainMark_Object_cap>(create_resource_address(&@dapp,Seed)).exten_cap;
        // let object_signer = &object::generate_signer_for_extending(object_extend);
        // debug::print(&object::address_to_object<ObjectCore>(address_of(object_signer)));
        // debug::print(borrow_global<Problem_set>(address1));
        // debug::print(&image_vector() );

        //increase_CHP(caller);
        //withdraw_CHC(signer::address_of(caller),user1);



        //del_object_owner(organisztion_signer);

        let obj_address = object::create_object_address(&create_resource_address(&@dapp,Seed),Seed);
        let obj_metadata = object::address_to_object<Metadata>(obj_address);

        // debug::print(&utf8(b"caller CHC Balance"));
        // debug::print(& primary_fungible_store::balance(signer::address_of(caller),obj_metadata));
        //
        // debug::print(&utf8(b"user CHC Balance"));
        // debug::print(& primary_fungible_store::balance(signer::address_of(user1),obj_metadata));
        debug::print(&utf8(b"Resources own"));
        debug::print(&is_owner(obj_metadata,create_resource_address(&@dapp,Seed)));

        debug::print(&utf8(b"Organization own"));
        debug::print(&is_owner(obj_metadata,signer::address_of(organisztion_signer)));

        debug::print(&utf8(b"User own"));
        debug::print(&is_owner(obj_metadata,signer::address_of(user1)));

        transfer_object_owner(organisztion_signer,signer::address_of(user1));

        debug::print(&utf8(b"Resources own"));
        debug::print(&is_owner(obj_metadata,create_resource_address(&@dapp,Seed)));

        debug::print(&utf8(b"Organization own"));
        debug::print(&is_owner(obj_metadata,signer::address_of(organisztion_signer)));

        debug::print(&utf8(b"User own"));
        debug::print(&is_owner(obj_metadata,signer::address_of(user1)));
    }

```
繼續調object 的用法

### 2024.09.26

最後兩天寫完transfer 和del obj 的fun了

```move

 public entry fun del_object_owner (caller:&signer) acquires Object_cap,  Resource_store_object {
        // let object_cap = &borrow_global<Object_cap>(signer::address_of(caller)).del_cap;
        // debug::print(&utf8(b"exist object cap"));
        // debug::print(&exists<Object_cap>(signer::address_of(caller)));
        let problem_set_object_address = borrow_global< Resource_store_object >(create_resource_address(&@dapp,Seed)).object;
        let  Object_cap { trans_cap,del_cap,exten_cap } = move_from<Object_cap>(problem_set_object_address);
        // let object_signer = &object::generate_signer_for_extending(&exten_cap);
        //let borrow_problem_set = borrow_global<Problem_set>(signer::address_of(object_signer));
        let object_core = object::address_to_object<ObjectCore>(problem_set_object_address);

        assert!(object::is_owner(object_core,signer::address_of(caller)) == true || signer::address_of(caller) == @admin, NOT_owner_or_admin );
        // debug::print(&utf8(b"exist object cap"));
        // debug::print(&object_cap);
        object::delete(del_cap);
    }
    public entry fun transfer_object_owner (caller:&signer,to:address) acquires Object_cap, Problem_set, Resource_store_object {
        let  Object_cap { trans_cap,del_cap,exten_cap } = move_from<Object_cap>(signer::address_of(caller));
        let object_signer = &object::generate_signer_for_extending(&exten_cap);
        let borrow_problem_set = borrow_global<Problem_set>(signer::address_of(object_signer));
        let problem_set_object_address = borrow_global< Resource_store_object >(create_resource_address(&@dapp,Seed)).object;
        let object_core = object::address_to_object<ObjectCore>(problem_set_object_address);
        assert!( borrow_problem_set.owner.address == signer::address_of(caller) || signer::address_of(caller) == @admin, NOT_owner_or_admin );
        let liner_transfer = object::generate_linear_transfer_ref(&trans_cap);

        move_to(object_signer,Object_cap{
            trans_cap,del_cap,exten_cap
        });
        object::transfer_with_ref(liner_transfer,to);
    }
```

### 2024.09.27

最後一天

完成了diffusion的 fun 和新的object合約
testnet :
`0x66cd3cc5d2d724d9eacc30a35cf61aef36c0fe69bc1c7ecb9444cae9a39aecd2` - chainmark
`0x7776f4ac2f3a13f751b966220b0e68e0b5688682c31e4f93cbf12ce1cea4a7b9` - diffusion

<!-- Content_END -->
