# vlsi1
Experiment No. 1
-- Company: 
-- Engineer: 
-- Create Date:    21:10:15 07/14/2024 
-- Design Name: 
-- Module Name:    alu_exp1 - Behavioral 
-- Project Name: 
-- Target Devices: 
-- Tool versions: 
-- Description: 
-- Dependencies: 
-- Revision: 
-- Revision 0.01 - File Created
-- Additional Comments:
----------------------------------------------------------------------------------
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.STD_LOGIC_ARITH.ALL;
use IEEE.STD_LOGIC_UNSIGNED.ALL;

---- Uncomment the following library declaration if instantiating
---- any Xilinx primitives in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity alu_exp1 is
    Port ( a : in  STD_LOGIC_VECTOR (3 downto 0);
           b : in  STD_LOGIC_VECTOR (3 downto 0);
           s : in  STD_LOGIC_VECTOR (2 downto 0);
           y : out  STD_LOGIC_VECTOR (3 downto 0));
end alu_exp1;

architecture Behavioral of alu_exp1 is
begin
process(a,b,s)
begin
case s is
when"000"=>
y<=a + b;
when"001"=>
y<=a - b;
when"010"=>
y<=a and b;
when"011"=>
y<=a nand b;
when"100"=>
y<=a xnor b;
when"101"=>
y<=a xnor b;
when"110"=>
y<=a or b;
when"111"=>
y<=a ;
when others=>
null;
end case;
end process;
end Behavioral;

--------------------------------------------------------------------------------
Test   bench
-- Company: 
-- Engineer:
-- Create Date:   21:40:27 07/14/2024
-- Design Name:   alu_exp1
-- Module Name:   C:/Xilinx92i/Epx1/aluTestBench.vhd
-- Project Name:  Epx1
-- Target Device:  
-- Tool versions:  
-- Description:   
-- VHDL Test Bench Created by ISE for module: alu_exp1
-- Dependencies:
-- Revision:
-- Revision 0.01 - File Created
-- Additional Comments:
-- Notes: 
-- This testbench has been automatically generated using types std_logic and
-- std_logic_vector for the ports of the unit under test.  Xilinx recommends 
-- that these types always be used for the top-level I/O of a design in order 
-- to guarantee that the testbench will bind correctly to the post-implementation 
-- simulation model.
--------------------------------------------------------------------------------
LIBRARY ieee;
USE ieee.std_logic_1164.ALL;
USE ieee.std_logic_unsigned.all;
USE ieee.numeric_std.ALL;

ENTITY aluTestBench_vhd IS
END aluTestBench_vhd;

ARCHITECTURE behavior OF aluTestBench_vhd IS 
	-- Component Declaration for the Unit Under Test (UUT)
	COMPONENT alu_exp1
	PORT(
		a : IN std_logic_vector(3 downto 0);
		b : IN std_logic_vector(3 downto 0);
		s : IN std_logic_vector(2 downto 0);          
		y : OUT std_logic_vector(3 downto 0)
		);
	END COMPONENT;

	--Inputs
	SIGNAL a :  std_logic_vector(3 downto 0) := (others=>'0');
	SIGNAL b :  std_logic_vector(3 downto 0) := (others=>'0');
	SIGNAL s :  std_logic_vector(2 downto 0) := (others=>'0');

	--Outputs
	SIGNAL y :  std_logic_vector(3 downto 0);

BEGIN
	-- Instantiate the Unit Under Test (UUT)
	uut: alu_exp1 PORT MAP(
		a => a,
		b => b,
		s => s,
		y => y
	);

	tb : PROCESS
	BEGIN
		-- Wait 100 ns for global reset to finish
		--wait for 100 ns;
		-- Place stimulus here
		a<="1111";
		b<="0000";
		s<="000";
		
		--wait for 50 ns;
		s<="000";
		wait for 50 ns;
		s<="001";
		wait for 50 ns;
		s<="010";
		wait for 50 ns;
		s<="011";
		wait for 50 ns;
		s<="100";
		wait for 50 ns;
		s<="101";
		wait for 50 ns;
		s<="110";
		wait for 50 ns;
		s<="111";
		wait for 50 ns;
		wait; -- will wait forever
	END PROCESS;

END;
