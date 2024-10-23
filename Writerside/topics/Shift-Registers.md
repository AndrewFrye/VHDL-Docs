# Shift Registers

A simple 4-bit shift register. Async active low reset.

###### Entity
```
entity shift_register is
    Port ( D : in STD_LOGIC_VECTOR (3 downto 0);
           CNTL : in STD_LOGIC_VECTOR (1 downto 0);
           CLK : in STD_LOGIC;
           RST : in STD_LOGIC;
           Q : out STD_LOGIC_VECTOR (3 downto 0));
end shift_register;
```

###### Architecture
```
architecture Behavioral of shift_register is
signal Q_Buff : std_logic_vector (3 downto 0);
begin
    Proc_Register : process (CLK, RST, CNTL)
        begin
        end process;
    Q <= Q_Buff;
end Behavioral;
```

###### Register Process
```
Proc_Register : process (CLK, RST, CNTL)
    begin
        if (RST = '0') then
            Q_Buff <= "0000";
        end if;
        if (rising_edge(CLK)) then
            with (CNTL) select
                Q_Buff <= D when "00",
                          '0' & Q_Buff(3 downto 1) when "01",
                          Q_Buff(2 downto 0) & '0' when "10",
                          Q_Buff when "11",
                          "0000" when others;
    end if;
end process;
```