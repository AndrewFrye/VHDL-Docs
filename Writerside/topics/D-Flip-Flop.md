# D Flip-Flop

###### Entity
```
entity Dflipflop is
    port ( CLK : in std_logic;
           D : in std_logic;
           Q : out std_logic);
end entity;
```

###### Architecture
```
architecture Dflipflop_arch of Dflipflopis
    begin
    Proc_Dflipflop: process (CLK)
    begin
        if (CLK’eventand CLK=`1`) then
            Q <= D;
        end if;
    end process;
end architecture;
```