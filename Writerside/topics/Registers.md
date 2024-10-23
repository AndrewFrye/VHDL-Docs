# Registers

8-bit register with Async active low reset.

###### Entity
```
entity Registers is
    port (
        clk : in std_logic;
        reset : in std_logic;
        enable : in std_logic;
        data_in : in std_logic_vector(7 downto 0);
        data_out : out std_logic_vector(7 downto 0)
    );
end entity Registers;
```

###### Architecture
```
architecture Behavioral of Registers is
    signal reg : std_logic_vector(7 downto 0);
        begin
        end process;
    data_out <= reg;
end architecture Behavioral;
```

###### Register Process
```
Proc_Register : process (CLK)
    begin
        if (reset = '0') then
            reg <= '0';
        elsif (rising_edge(CLK)) then
            data_out <= D;
            end if;
    end process;
```