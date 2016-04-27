----------------------------------------------------------------------------------
-- Company: 
-- Engineer: 
-- 
-- Create Date:    16:05:31 04/27/2016 
-- Design Name: 
-- Module Name:    mpx - Behavioral 
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

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--use IEEE.NUMERIC_STD.ALL;

-- Uncomment the following library declaration if instantiating
-- any Xilinx primitives in this code.
--library UNISIM;
--use UNISIM.VComponents.all;

entity mpx is
    Port ( mpx_crs2 : in  STD_LOGIC_VECTOR (31 downto 0);
           mpx_i : in  STD_LOGIC;
           mpx_seu : in  STD_LOGIC_VECTOR (31 downto 0);
           mpx_out : out  STD_LOGIC_VECTOR (31 downto 0));
end mpx;

architecture Behavioral of mpx is

begin
process(mpx_crs2,mpx_seu,mpx_i)
	begin
		if(mpx_i= '1')then
			mpx_out <= mpx_seu;
		else
			if(mpx_i= '0')then
				mpx_out <= mpx_crs2;
			end if;
		end if;
	end process;


end Behavioral;

