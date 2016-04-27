----------------------------------------------------------------------------------
-- Company: 
-- Engineer: 
-- 
-- Create Date:    01:01:28 04/26/2016 
-- Design Name: 
-- Module Name:    rf - Behavioral 
-- Project Name: 
-- Target Devices: 
-- Tool versions: 
-- Description: 
--
-- Dependencies: 
--
-- Revision: 
-- Revision 0.01 - File Created
-- Additional Comments: 
--
----------------------------------------------------------------------------------
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.STD_LOGIC_UNSIGNED.ALL;

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--use IEEE.NUMERIC_STD.ALL;

-- Uncomment the following library declaration if instantiating
-- any Xilinx primitives in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity rf is
    Port ( rs1 : in  STD_LOGIC_VECTOR (4 downto 0);
           rs2 : in  STD_LOGIC_VECTOR (4 downto 0);
           rd : in  STD_LOGIC_VECTOR (4 downto 0);
           in1 : in  STD_LOGIC_VECTOR (31 downto 0);
           crs1 : out  STD_LOGIC_VECTOR (31 downto 0);
           crs2 : out  STD_LOGIC_VECTOR (31 downto 0);
           reset : in  STD_LOGIC);
end rf;

architecture Behavioral of rf is
type ram_type is array (0 to 39) of std_logic_vector (31 downto 0);
	signal registers : ram_type := (others => x"00000000");
	

begin
  --,reset,registerSource1,registerSource2,registerDestination,writeEnable,dataToWrite
	process(reset,rs1,rs2,rd,in1)
	begin
		
			if(reset = '1')then
				crs1 <= (others=>'0');
				crs2 <= (others=>'0');
				
				registers <= (others => x"00000000");
			else
				crs1 <= registers(conv_integer(rs1));
				crs2 <= registers(conv_integer(rs2));
				if(rd /= "000000")then
					registers(conv_integer(rd)) <= in1;
				end if;
			end if;
		
		end process;
end Behavioral;

