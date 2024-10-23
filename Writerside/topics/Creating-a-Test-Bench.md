# Creating a Test Bench

A simple test bench example for the sample 4-state <a href="State-Machine.md">State Machine</a>.
When using a test bench ensure the test bench is not the top source so the main entity definition
is used.

###### Entity

This is a very barebones entity because it is only being used to drive another.

```vhdl
entity TestBench is
--  Port ( );
end TestBench;
```

###### Architecture

```vhdl
architecture Behavioral of TestBench is

--Component instantiation for the StateMachine entity
component StateMachine
    port (CLK : in std_logic;
          Input, Reset : in std_logic;
          T : out std_logic);
end component;

--Declaring signals for the test bench to use to drive the main entity
signal T_TB : std_logic;
signal Input_TB : std_logic;
signal CLK_TB : std_logic;

Clock : process
    begin
    end process;
    
TB : process
    begin
    end process;

end Behavioral;
```

###### Clock Process

```vhdl
CLOCK : process
    begin
      for i in 1 to 4 loop
        CLK_TB <= '0';
        wait for 50 ns;
    
        CLK_TB <= '1';
        wait for 50 ns;
      end loop;
    end process;
```

###### Test Bench Process

```vhdl
TB : process 
    begin
      Input_TB <= '0';
      RST_TB <= '0';    -- clk 1: reset state machine to A
      wait for 100 ns;
      
      Input_TB <= '0';
      RST_TB <= '1';    -- clk 2: Stop the reset and go to B
      wait for 100 ns;
      
      Input_TB <= '0';      -- clk 3: go back to A
      wait for 100 ns;
      
      Input_TB <= '1';      -- clk 4: go to B
      wait for 100 ns;
      
      Input_TB <= '1';       -- clk 5: go to C
      wait for 100 ns; 
      
      Input_TB <= '1';       -- clk 6: go to D
      wait for 100 ns;     
      
      Input_TB <= '1';       -- clk 7: go to A
      wait for 100 ns;     
    end process;
```