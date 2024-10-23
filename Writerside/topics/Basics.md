# Basics

###### Entity
```vhdl
entity sample is
    port (CLK : in std_logic;
          Input, Reset : in std_logic;
          T : out std_logic);
end entity;
```

###### Component initialization
The component should follow the same ports and name as the entity it is based on.<br>

Before the begin statement in the architecture,
```vhdl
component sample
    port (CLK : in std_logic;
          Input, Reset : in std_logic;
          T : out std_logic);
end component;
```

After the begin statement in the architecture,
```vhdl
DUT : sample port map (UP => UP_TB, DOWN => DOWN_TB, CLK => CLK_TB, 
        RST => RST_TB, Speed => Speed_TB, FR => FR_TB);
```