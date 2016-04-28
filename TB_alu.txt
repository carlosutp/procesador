--------------------------------------------------------------------------------
-- Company: 
-- Engineer:
--
-- Create Date:   16:36:48 04/27/2016
-- Design Name:   
-- Module Name:   C:/Users/carlos/Desktop/procesador/prosesador1/tb_alu.vhd
-- Project Name:  prosesador1
-- Target Device:  
-- Tool versions:  
-- Description:   
-- 
-- VHDL Test Bench Created by ISE for module: alu
-- 
-- Dependencies:
-- 
-- Revision:
-- Revision 0.01 - File Created
-- Additional Comments:
--
-- Notes: 
-- This testbench has been automatically generated using types std_logic and
-- std_logic_vector for the ports of the unit under test.  Xilinx recommends
-- that these types always be used for the top-level I/O of a design in order
-- to guarantee that the testbench will bind correctly to the post-implementation 
-- simulation model.
--------------------------------------------------------------------------------
LIBRARY ieee;
USE ieee.std_logic_1164.ALL;
 
-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--USE ieee.numeric_std.ALL;
 
ENTITY tb_alu IS
END tb_alu;
 
ARCHITECTURE behavior OF tb_alu IS 
 
    -- Component Declaration for the Unit Under Test (UUT)
 
    COMPONENT alu
    PORT(
         alu_aluop : IN  std_logic_vector(5 downto 0);
         alu_crs1 : IN  std_logic_vector(31 downto 0);
         alu_mpx : IN  std_logic_vector(31 downto 0);
         alu_out : OUT  std_logic_vector(31 downto 0)
        );
    END COMPONENT;
    

   --Inputs
   signal alu_aluop : std_logic_vector(5 downto 0) := (others => '0');
   signal alu_crs1 : std_logic_vector(31 downto 0) := (others => '0');
   signal alu_mpx : std_logic_vector(31 downto 0) := (others => '0');

 	--Outputs
   signal alu_out : std_logic_vector(31 downto 0);
   -- No clocks detected in port list. Replace <clock> below with 
   -- appropriate port name 
 
   --constant <clock>_period : time := 10 ns;
 
BEGIN
 
	-- Instantiate the Unit Under Test (UUT)
   uut: alu PORT MAP (
          alu_aluop => alu_aluop,
          alu_crs1 => alu_crs1,
          alu_mpx => alu_mpx,
          alu_out => alu_out
        );

   -- Clock process definitions
   --<clock>_process :process
   --begin
	--	<clock> <= '0';
	--	wait for <clock>_period/2;
	--	<clock> <= '1';
	--	wait for <clock>_period/2;
   --end process;
 
 
   -- Stimulus process
   stim_proc: process
   begin		 
      wait for 100 ns;	
      
		alu_crs1 <= X"00000342";
		alu_mpx <= X"00000555";
	   alu_aluop <= "000000";
		wait for 100 ns;
      wait;
   end process;

END;
